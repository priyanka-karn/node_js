.PHONY: aws
aws: lambda-proxy

.PHONY: lambda-proxy
lambda-proxy:
	cd LambdaProxy; mkdir -p node_modules; npm install https://cdn.sheetjs.com/xlsx-latest/xlsx-latest.tgz busboy; sam local start-api; cd -

.PHONY: init-azure
init-azure:
	cd AzureHTTPTrigger; mkdir -p node_modules; npm install https://cdn.sheetjs.com/xlsx-latest/xlsx-latest.tgz formidable fs

.PHONY: azure
azure: init-azure
	func start

.PHONY: azure-server
azure-server:
	mkdir -p /tmp/azurite
	azurite -l /tmp/azurite

FILES=$(filter-out xlsx.full.min.js,$(wildcard *.js)) $(wildcard *.html)
.PHONY: lint
lint: $(FILES)
	eslint $(FILES)

.PHONY: clean
clean:
	rm -f *.db *.xlsx *.csv

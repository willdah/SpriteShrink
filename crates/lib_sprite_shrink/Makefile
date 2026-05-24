.PHONY: help build release lint fmt test check clean

PKG := sprite_shrink

##@ General

help: ## Print this help message
	@awk 'BEGIN {FS = ":.*?## "; printf "\nUsage: \033[1mmake\033[0m \033[36m<target>\033[0m\n"} \
	     /^##@/ {printf "\n\033[1m%s\033[0m\n", substr($$0, 5); next} \
	     /^[a-zA-Z_-]+:.*?## / {printf "  \033[36m%-26s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST)
	@printf "\n"

##@ Build

build: ## Build sprite_shrink (dev profile)
	cargo build -p $(PKG)

release: ## Build sprite_shrink (release profile)
	cargo build -p $(PKG) --release

##@ Quality

lint: ## Check formatting and run Clippy (-D warnings)
	cargo fmt -p $(PKG) -- --check
	cargo clippy -p $(PKG) --all-targets -- -D warnings

fmt: ## Format source code
	cargo fmt -p $(PKG)

test: ## Run unit tests
	cargo test -p $(PKG)

check: lint test ## Run lint and test

##@ Misc

clean: ## Remove build artifacts
	cargo clean -p $(PKG)

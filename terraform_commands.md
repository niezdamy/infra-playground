## download plugins into folder .terraform

```bash
terraform init
```

## set logging level: TRACE, INFO, WARN, ERROR

```bash
export TF_LOG="DEBUG"
```

## dry run

```bash
terraform plan
terraform plan -out will-by-applied.zip
```

## apply configuration

```bash
terraform apply
terraform apply -auto-approve
terraform apply will-by-applied.zip
```

## apply state from another file

```bash
terraform state push -force terraform.tfstate
```

## remove all resources

```bash
terraform destroy
```

## visualisation for resources

```bash
sudo apt install graphviz

terraform graph | dot -Tpng > out.png
```

## list of providers

```bash
terraform providers
```

## validation of current source code

```
terraform validate
```

## show resources get all variables for using in resources

```bash
terraform show

terraform console
```

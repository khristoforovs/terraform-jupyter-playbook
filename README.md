# Terraform manifest to deploy VM with Jupyter Notebook in Yandex Cloud

## How to:
1. `git clone` the repo
2. Get the [Yandex Cloud authentication data](https://cloud.yandex.ru/docs/compute/operations/vm-connect/ssh?from=int-console-help-center-or-nav)
3. `terraform init`
4. Insert user related information into manifest: 
    * Type `ssh-keygen -t ed25519` then insert path to the public key into `meta.yml`
    * Choose any password to the Jupyter and generate the hash. 
        ```python
        In [1]: from notebook.auth import passwd
        In [2]: passwd()
        Enter password:  ****
        Verify password: ****
        Out[2]: 'sha1:67c9e60bb8b6:9ffede0825894254b2e042ea597d771089e11aed'
        ```
        Then insert generated string into `docker-compose.yml`
5. `terraform apply`
6. Connect the Jupyter notebook via provided external IP
7. To finish the usage, type `terraform destroy`
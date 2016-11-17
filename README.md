# Wordpress+PHP+MySQL+Nginx

## IMPORTANT: This role should only be used for deploy as it will reset all signed cookies every time it is used

Set up a new group then put it in group_vars and vault the wp_db_password

```EDITOR=/bin/nano ansible-vault create group_vars/group/vault.yml```

Configure all the other settings in main.yml and deploy

```
# Wordpress version
wp_version: 4.5.2
wp_sha256sum: 1a4d9f05142701e72413609cc30029f66af0f3b29d4ff051e888f48026d20ac9

# Wordpress database settings
wp_db_name: wordpress 
wp_db_user: wordpress
wp_db_password: "{{vault_wp_db_password}}"

# MySQL port
mysql_port: 3306

# hostname that nginx will respond to
server_hostname: www.example.com

# set true to disable automatic updates
auto_up_disable: false

#Define Core Update Level
#true  = Development, minor, and major updates are all enabled
#false = Development, minor, and major updates are all disabled
#minor = Minor updates are enabled, devel
core_update_level: true

#Define ssh key for sftp wordpress user
wp_user_ssh_key: "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCzZye57La/rRO3Lp43UKA/V6eBEa+9BjnFrTnWyQp3uK/i1Pe3hs6bTq3gQlIjhI35LyYYnNxEPpyYZkoxTk0yl4W3HEMe4nIs96UuqOJlSSiI2Sfd1rqgkkBjhZrIxqtASBnRnuomEhvJe8ENGZszNLh3B9m5Rn5SAGF3fUMW4dLA9zWX5+DRa3wqf+V62FOyrL60vma2yfZycsmPWppK4Y/Kt2FMY708Ppfk2vK/oSQxGxvkVUdymQmT/Z3UHNohCfZlBtJ6mAOuA/e0QY7WG/+0aUXEyRkFCie4K9v2ZC2pJdhKA7DKRXLbTssKeGZCd0QhbcA8cgw9WQ6VUQLb"
```
My Ansible LAMP Playbook

An Ansible playbook that automatically sets up a LAMP server (Linux, Apache, MySQL, PHP) and also installs WordPress on it. Built as a portfolio piece for a web developer role.

Instead of installing everything manually command by command, you can run one command and Ansible does it all automatically.

What it basically does:

Running `ansible-playbook -i inventory.ini site.yml` will automatically

- Update all server packages
- Set the timezone to Europe/Helsinki
- Install Apache web server on port 8080
- Install PHP as well as all the extensions WordPress needs
- Install MySQL and create a database and a user for WordPress
- Download and configure WordPress

My Project's structure:

ansible-lamp-playbook/
├── site.yml              # Main playbook — defines what runs and in what order
├── inventory.ini         # Defines which server to target
├── vars/
│   └── main.yml          # Variables: database name, user, password
└── roles/
    ├── common/           # Updates packages, sets timezone
    ├── apache/           # Installs and configures Apache
    ├── php/              # Installs PHP and extensions
    ├── mysql/            # Installs MySQL, creates database and user
    └── wordpress/        # Downloads and configures WordPress


How to run it though?

What you need: Ubuntu/Debian Linux, Ansible installed

```
{Install Ansible}
sudo apt-get install ansible

{Clone the repo}
git clone git@github.com:Meromooo/ansible-lamp-playbook.git
cd ansible-lamp-playbook

{Run the playbook}
ansible-playbook -i inventory.ini site.yml
```

Once it finishes, WordPress will be available at `http://localhost:8080`.

What did I learn from this project?

This was my first time using Ansible so I learned how playbooks and roles work, what idempotency means (you can run the playbook multiple times without breaking anything) and also on how to automate server setup with YAML instead of just running commands manually over and over.

Why is it connected to Helsinki City Library?

Ansible is mentioned in the Helsinki City Library civil service job posting as a tool used to maintain their Debian servers so this project shows I can write and run Ansible playbooks to automate every server configuration.
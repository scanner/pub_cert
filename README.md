# pub_cert
Ansible role that uses the ansible 'letsencrypt' module to automate generating SSL certificates

This is intended to be invoked via the `include_role` directive in a
play or other role.

Right now this only supports the `http-01` challenge method. 

Most aspects of the certificate being generated are passed via
variables. Look in `defaults/main.yml` for all the possible variables.

Invocation looks like:

    - name: Install SSL Certificate Files
      include_role:
        name: pub_cert
      vars:
        common_name: "example.com"
        pubcert_challenge_dir: "/usr/local/www/htdocs"
        subject_alt_names:
          - name: "san-name.example.com"
            challenge_dir: "/usr/local/www/san-name/htdocs"

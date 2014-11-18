Mandrill Relay
=========

Uses postfix to relay all email on the host through Mandrill. Essentially creates a 

Requirements
------------

Requires an active mandrill account and should have an API key ready. Additionally for proper deliverability SPF and DKIM records should be setup correctly for the mandrill service on the domain used.

Tested on CentOS 6, Ubuntu 14.04 and Debian 7. 

Role Variables
--------------

Required:
- mandrill\_relay\_username = The username to use for mandrill relaying
- mandrill\_relay\_apikey = The api key to use when relaying email for Mandrill (ideally use Ansible Vault).

Optional: 
- mandrill\_relay\_hostname = The hostname of this machine
- mandrill\_relay\_myorigin = The origin to use when relaying email (default: $mydomain)
- mandrill\_relay\_mynetworks = Networks to deliver mail for (defaults to loopback)
- mandrill\_relay\_mydestinations = Networks that we deliver mail for locally (leave blank for a nullmailer)
- mandrill\_relay\_if = The interface to listen for incoming mails on (default: loopback-only)
- mandrill\_relay\_server = The server that is used from Mandrill app (smtp.mandrillapp.com is the default)
- mandrill\_relay\_tls\_key = Keyfile (defaults to snakeoil)
- mandrill\_relay\_tls\_cert = Certfile (defaults to snakeoil)

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: mandrill_relay, mandrill_relay_username: mandrill@mandrillapp.com, mandrill_relay_apikey=APIKEY }

License
-------

BSD

Author Information
------------------

Linus Kendall <git@linuskendall.com>

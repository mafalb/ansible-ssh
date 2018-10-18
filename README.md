
### ssh/known_hosts

ssh:
  known_hosts:
    managed: false
    context: user
    
  config:
    GlobalKnownHostsFile: /etc/ssh/known_hosts
    UserKnownHostsFile: ~/.ssh/known_hosts
    
- role: ssh/known_hosts
  ssh:
    system:
    config:
      

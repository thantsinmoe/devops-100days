Task : Install SElinux and edit configuration to disable SElinux
cmd >> hostnamectl   # check OS type (eg: Ubuntu or Centos)
cmd >> sudo yum install policycoreutils policycoreutils-python setools setools-console setroubleshoot   # install necessary SElinux package on Centos
cmd >>     sudo yum install selinux-policy-targeted

SElinux config file directory - /etc/selinux/config

edit & save config >> SELINUX=disabled  #Change enforcing to disabled

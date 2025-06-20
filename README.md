# agent-ocp

set tabstop=2       " A tab character appears as 2 spaces
set shiftwidth=2    " Indent/outdent by 2 spaces
set expandtab       " Convert tabs to spaces
set autoindent      " Copy indent from current line when starting a new one
set smartindent     " Smart auto-indenting on new lines

cat pull-secret.txt | jq -c .

jq . pull-secret.txt > pull-secret.json


#DNSMASQ example
interface=eno1
dhcp-range=192.168.4.100,192.168.4.200,12h
dhcp-host=00:11:22:33:44:55,192.168.4.126,sno
address=/sno.example.com/192.168.4.126
ptr-record=126.4.168.192.in-addr.arpa,sno.example.com

openshift-install agent create install-config
openshift-install agent create image
openshift-install --dir . agent wait-for install-complete --log-level debug

🔁 Summary
Step	Task
1	Prepare environment and download tools
2	Create install-config.yaml
3	Create agent-config.yaml with networking
4	Generate the image using the Agent Installer
5	Boot RHEL system from ISO
6	Wait for install to complete
7	Access the cluster using oc or browser

# ansiblefest2019
Roles from my ansiblefest 2019 presentation, Automating Firewall Requests with Tower

Our F5 Virtual Server, ACI EPG and ACI BD naming conventions in F5 and ACI will help you understand the regex and parsing in the roles a bit more:

Virtual Server: 
ACI EPG: "EPG-{{ EPG_NAME }}"
ACI BD:  "BD-{{ EPG_NAME }}-{{ TENANT_NAME }}"

When we import the EPG/BD and VIPs in Palo Panorama we use the following naming convention:

Bridge Domain (BD)/ EPG
Object Syntax: [DATACENTER]_[TENANT]_[BDNAME]_[SUBNET]_[CIDR_MASK]
Group Syntax: [TENANT]_[BDNAME]

Virtual Server:
[DATACENTER]_[TENANT]_VIP_[FQDN]_[IP]_[CIDR_MASK]

Internet Address Objects
Object Syntax: Subnets and Single IP: INTERNET_[SECONDLEVELDOMAIN]_[TLD]_[IP]_[CIDR_MASK]
Object Syntax: IP Range: INTERNET_[SECONDLEVELDOMAIN]_[TLD]_[STARTIP]_[ENDIP]
Group Syntax: INTERNET_[SECONDLEVELDOMAIN]_[TLD]_[A RECORD]

Service Objects
Service Syntax Single Port: [PROTOCOL]_[PORT]
Service Syntax Port Range: [PROTOCOL]_[STARTPORT]_[ENDPORT]
Application Objects
Application syntax
Application Groups syntax: [PROTOCOL]_[PORT]_[NAME]

AD groups for User-ID:
Only use security groups in a specific OU which have a name of "sec-ia-{{ ad_group_name }}"
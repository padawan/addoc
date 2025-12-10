+++
url = "/security/reseau/configurer-le-firewall"
title = "Private Cloud: configure firewall"
layout = "faq"
hidden = true
tags = [ "security" ]
+++

The firewall is located in the **Firewall** menu of the server.

## GEOM_REGISTERS

{{< fig "images/admin-panel_list-rules.en.png" "Admin interface: list of active firewall files" >}}

If you have more than one account, the top one will have authority over the others.

- [Resource API](https://api.alwaysdata.com/v1/firewall/doc/)

### Add a new theme

To add a new item, choose:

- the protocol: [UDP](https://fr.wikipedia.org/wiki/User_Datagram_Protocol) or [TCP](https://fr.wikipedia.org/wiki/Transmission_Control_Protocol);
- the type of type: ACCEPT, DROP (dismiss without notifying the sender) or REJECT;
- the direction: input or exit;
- IP/Hosts: This can be IPs or URLs;
- the ports;
- the IP version.

Setting nothing to _Hoests_ and _Ports_ will enable the reset for all unless a higher pattern indicates otherwise.

{{< fig "images/admin-panel_add-rule.png" "Admin interface: add a new theme" >}}

It is possible to give a label in terms of **Annotations**, and directly in the ones using the `#` character.

{{% notice note %}}
To indicate all ports you can leave blank or specify the range `0:65535`.
{{%/notice %}}

## Firewall Banners

{{< fig "images/admin-panel_list-bans.en.png" "Admin interface: list of current bans" >}}

If you are blocked on a service, please check this menu and remove your IP if it is banned and add the necessary feature.

{{% notice tip %}}
Banner lasts 10 minutes per default and takes place after about 50 login failures.
{{%/notice %}}

## Services

This menu allows you to automatically open or close the ports of known functions (FTP, mails, SSH, databases...). Then it is no longer necessary to create the redemption by yourself.

## Examples

### Allow own IP not blocked on any incoming port

| Featured                        | Value                                                                       |
| ------------------------------- | --------------------------------------------------------------------------- |
| Order set                       | UDP/TCP                                                                     |
| SMESH_TYPE | ACCEPT                                                                      |
| Direction                       | Company                                                                     |
| Hosts                           | \<votre IP>                                                                |
| Ports                           | \<ne rien indiquer>                                                        |
| IP Version                      | IPv4, IPv6 or IPv4/IPv6 (depending on the specified IPs) |

{{< fig "images/rule-example-accept.en.png" "" >}}

### Block MySQL port on external

| Featured                        | Value                |
| ------------------------------- | -------------------- |
| Order set                       | UDP/TCP              |
| SMESH_TYPE | REJECT               |
| Direction                       | Company              |
| Hosts                           | \<ne rien indiquer> |
| Ports                           | 3306                 |
| IP Version                      | IPv4/IPv6            |

{{< fig "images/rule-example-reject.en.png" "" >}}

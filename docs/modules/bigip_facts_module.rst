.. _bigip_facts:


bigip_facts - Collect facts from F5 BIG-IP devices
++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Collect facts from F5 BIG-IP devices via iControl SOAP API


Requirements (on host that executes module)
-------------------------------------------

  * bigsuds


Options
-------

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">parameter</th>
    <th class="head">required</th>
    <th class="head">default</th>
    <th class="head">choices</th>
    <th class="head">comments</th>
    </tr>
            <tr>
    <td>filter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Shell-style glob matching string used to filter fact keys. Not applicable for software and system_info fact categories.</div></td></tr>
            <tr>
    <td>include<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>address_class</li><li>certificate</li><li>client_ssl_profile</li><li>device</li><li>device_group</li><li>interface</li><li>key</li><li>node</li><li>pool</li><li>rule</li><li>self_ip</li><li>software</li><li>system_info</li><li>traffic_group</li><li>trunk</li><li>virtual_address</li><li>virtual_server</li><li>vlan</li></ul></td>
        <td><div>Fact category or list of categories to collect</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>BIG-IP password</div></td></tr>
            <tr>
    <td>server<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>BIG-IP host</div></td></tr>
            <tr>
    <td>server_port<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>443</td>
        <td><ul></ul></td>
        <td><div>BIG-IP server port</div></td></tr>
            <tr>
    <td>session<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>BIG-IP session support; may be useful to avoid concurrency issues in certain circumstances.</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>BIG-IP username</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites.  Prior to 2.0, this module would always validate on python &gt;= 2.7.9 and never validate on python &lt;= 2.7.8</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    ## playbook task examples:
    
    ---
    # file bigip-test.yml
    # ...
    - hosts: bigip-test
      tasks:
      - name: Collect BIG-IP facts
        local_action: >
          bigip_facts
          server=lb.mydomain.com
          user=admin
          password=mysecret
          include=interface,vlan
    


Notes
-----

.. note:: Requires BIG-IP software version >= 11.4
.. note:: F5 developed module 'bigsuds' required (see http://devcentral.f5.com)
.. note:: Best run as a local_action in your playbook
.. note:: Tested with manager and above account privilege level


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.


.. _bigip_gtm_monitor_https:


bigip_gtm_monitor_https - Manages F5 BIG-IP GTM https monitors
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.6


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages F5 BIG-IP GTM https monitors.


Requirements (on host that executes module)
-------------------------------------------

  * f5-sdk >= 3.0.9


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
                <tr><td>cipher_list<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the list of ciphers for this monitor.</div><div>The items in the cipher list are separated with the colon <code>:</code> symbol.</div><div>When creating a new monitor, if this parameter is not specified, the default list is <code>DEFAULT:+SHA:+3DES:+kEDH</code>.</div>        </td></tr>
                <tr><td>client_cert<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies a fully-qualified path for a client certificate that the monitor sends to the target SSL server.</div>        </td></tr>
                <tr><td>client_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies a key for a client certificate that the monitor sends to the target SSL server.</div>        </td></tr>
                <tr><td>compatibility<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Specifies, when enabled, that the SSL options setting (in OpenSSL) is set to <b>all</b>.</div><div>When creating a new monitor, if this value is not specified, the default is <code>yes</code></div>        </td></tr>
                <tr><td>ignore_down_response<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Specifies that the monitor allows more than one probe attempt per interval.</div><div>When <code>yes</code>, specifies that the monitor ignores down responses for the duration of the monitor timeout. Once the monitor timeout is reached without the system receiving an up response, the system marks the object down.</div><div>When <code>no</code>, specifies that the monitor immediately marks an object down when it receives a down response.</div><div>When creating a new monitor, if this parameter is not provided, then the default value will be <code>no</code>.</div>        </td></tr>
                <tr><td>interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The interval specifying how frequently the monitor instance of this template will run.</div><div>If this parameter is not provided when creating a new monitor, then the default value will be 30.</div><div>This value <b>must</b> be less than the <code>timeout</code> value.</div>        </td></tr>
                <tr><td>ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>IP address part of the IP/port definition. If this parameter is not provided when creating a new monitor, then the default value will be &#x27;*&#x27;.</div><div>If this value is an IP address, then a <code>port</code> number must be specified.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Monitor name.</div>        </td></tr>
                <tr><td>parent<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/Common/https</td>
        <td></td>
        <td><div>The parent template of this monitor template. Once this value has been set, it cannot be changed. By default, this value is the <code>tcp</code> parent on the <code>Common</code> partition.</div>        </td></tr>
                <tr><td>partition<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Common</td>
        <td></td>
        <td><div>Device partition to manage resources on.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The password for the user account used to connect to the BIG-IP. You can omit this option if the environment variable <code>F5_PASSWORD</code> is set.</div></br>
    <div style="font-size: small;">aliases: pass, pwd<div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Port address part of the IP/port definition. If this parameter is not provided when creating a new monitor, then the default value will be &#x27;*&#x27;. Note that if specifying an IP address, a value between 1 and 65535 must be specified.</div>        </td></tr>
                <tr><td>probe_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the number of seconds after which the system times out the probe request to the system.</div><div>When creating a new monitor, if this parameter is not provided, then the default value will be <code>5</code>.</div>        </td></tr>
                <tr><td rowspan="2">provider<br/><div style="font-size: small;"> (added in 2.5)</div></td>
    <td>no</td>
    <td></td><td></td>
    <td> <div>A dict object containing connection details.</div>    </tr>
    <tr>
    <td colspan="5">
    <table border=1 cellpadding=4>
    <caption><b>Dictionary object provider</b></caption>
    <tr>
    <th class="head">parameter</th>
    <th class="head">required</th>
    <th class="head">default</th>
    <th class="head">choices</th>
    <th class="head">comments</th>
    </tr>
                    <tr><td>password<br/><div style="font-size: small;"></div></td>
        <td>yes</td>
        <td></td>
                <td></td>
                <td><div>The password for the user account used to connect to the BIG-IP. You can omit this option if the environment variable <code>F5_PASSWORD</code> is set.</div>        </td></tr>
                    <tr><td>server<br/><div style="font-size: small;"></div></td>
        <td>yes</td>
        <td></td>
                <td></td>
                <td><div>The BIG-IP host. You can omit this option if the environment variable <code>F5_SERVER</code> is set.</div>        </td></tr>
                    <tr><td>server_port<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>443</td>
                <td></td>
                <td><div>The BIG-IP server port. You can omit this option if the environment variable <code>F5_SERVER_PORT</code> is set.</div>        </td></tr>
                    <tr><td>user<br/><div style="font-size: small;"></div></td>
        <td>yes</td>
        <td></td>
                <td></td>
                <td><div>The username to connect to the BIG-IP with. This user must have administrative privileges on the device. You can omit this option if the environment variable <code>F5_USER</code> is set.</div>        </td></tr>
                    <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>yes</td>
                <td><ul><li>yes</li><li>no</li></ul></td>
                <td><div>If <code>no</code>, SSL certificates will not be validated. Use this only on personally controlled sites using self-signed certificates. You can omit this option if the environment variable <code>F5_VALIDATE_CERTS</code> is set.</div>        </td></tr>
                    <tr><td>timeout<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>10</td>
                <td></td>
                <td><div>Specifies the timeout in seconds for communicating with the network device for either connecting or sending commands.  If the timeout is exceeded before the operation is completed, the module will error.</div>        </td></tr>
                    <tr><td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>Specifies the SSH keyfile to use to authenticate the connection to the remote device.  This argument is only used for <em>cli</em> transports. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div>        </td></tr>
                    <tr><td>transport<br/><div style="font-size: small;"></div></td>
        <td>yes</td>
        <td>cli</td>
                <td><ul><li>rest</li><li>cli</li></ul></td>
                <td><div>Configures the transport connection to use when connecting to the remote device.</div>        </td></tr>
        </table>
    </td>
    </tr>
        </td></tr>
                <tr><td>receive<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The receive string for the monitor call.</div>        </td></tr>
                <tr><td>reverse<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Instructs the system to mark the target resource down when the test is successful. This setting is useful, for example, if the content on your web site home page is dynamic and changes frequently, you may want to set up a reverse ECV service check that looks for the string Error.</div><div>A match for this string means that the web server was down.</div><div>To use this option, you must specify values for <code>send</code> and <code>receive</code>.</div>        </td></tr>
                <tr><td>send<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The send string for the monitor call.</div><div>When creating a new monitor, if this parameter is not provided, the default of <code>GET /\r\n</code> will be used.</div>        </td></tr>
                <tr><td>server<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The BIG-IP host. You can omit this option if the environment variable <code>F5_SERVER</code> is set.</div>        </td></tr>
                <tr><td>server_port<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>443</td>
        <td></td>
        <td><div>The BIG-IP server port. You can omit this option if the environment variable <code>F5_SERVER_PORT</code> is set.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>When <code>present</code>, ensures that the monitor exists.</div><div>When <code>absent</code>, ensures the monitor is removed.</div>        </td></tr>
                <tr><td>target_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the password, if the monitored target requires authentication.</div>        </td></tr>
                <tr><td>target_username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the user name, if the monitored target requires authentication.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The number of seconds in which the node or service must respond to the monitor request. If the target responds within the set time period, it is considered up. If the target does not respond within the set time period, it is considered down. You can change this number to any number you want, however, it should be 3 times the interval number of seconds plus 1 second.</div><div>If this parameter is not provided when creating a new monitor, then the default value will be 120.</div>        </td></tr>
                <tr><td>transparent<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies whether the monitor operates in transparent mode.</div><div>A monitor in transparent mode directs traffic through the associated pool members or nodes (usually a router or firewall) to the aliased destination (that is, it probes the <code>ip</code>-<code>port</code> combination specified in the monitor).</div><div>If the monitor cannot successfully reach the aliased destination, the pool member or node through which the monitor traffic was sent is marked down.</div><div>When creating a new monitor, if this parameter is not provided, then the default value will be <code>no</code>.</div>        </td></tr>
                <tr><td>update_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>always</td>
        <td><ul><li>always</li><li>on_create</li></ul></td>
        <td><div><code>always</code> will update passwords if the <code>target_password</code> is specified.</div><div><code>on_create</code> will only set the password for newly created monitors.</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The username to connect to the BIG-IP with. This user must have administrative privileges on the device. You can omit this option if the environment variable <code>F5_USER</code> is set.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. Use this only on personally controlled sites using self-signed certificates. You can omit this option if the environment variable <code>F5_VALIDATE_CERTS</code> is set.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    - name: Create a GTM HTTPS monitor
      bigip_gtm_monitor_https:
        name: my_monitor
        ip: 1.1.1.1
        port: 80
        send: my send string
        receive: my receive string
        password: secret
        server: lb.mydomain.com
        state: present
        user: admin
      delegate_to: localhost

    - name: Remove HTTPS Monitor
      bigip_gtm_monitor_https:
        name: my_monitor
        state: absent
        server: lb.mydomain.com
        user: admin
        password: secret
      delegate_to: localhost

    - name: Add HTTPS monitor for all addresses, port 514
      bigip_gtm_monitor_https:
        name: my_monitor
        server: lb.mydomain.com
        user: admin
        port: 514
        password: secret
      delegate_to: localhost


Return Values
-------------

Common return values are `documented here <http://docs.ansible.com/ansible/latest/common_return_values.html>`_, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> parent </td>
        <td> New parent template of the monitor. </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> https </td>
    </tr>
            <tr>
        <td> ip </td>
        <td> The new IP of IP/port definition. </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> 10.12.13.14 </td>
    </tr>
            <tr>
        <td> port </td>
        <td> The new port the monitor checks the resource on. </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> 8080 </td>
    </tr>
            <tr>
        <td> interval </td>
        <td> The new interval in which to run the monitor check. </td>
        <td align=center> changed </td>
        <td align=center> int </td>
        <td align=center> 2 </td>
    </tr>
            <tr>
        <td> timeout </td>
        <td> The new timeout in which the remote system must respond to the monitor. </td>
        <td align=center> changed </td>
        <td align=center> int </td>
        <td align=center> 10 </td>
    </tr>
            <tr>
        <td> ignore_down_response </td>
        <td> Whether to ignore the down response or not. </td>
        <td align=center> changed </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> send </td>
        <td> The new send string for this monitor. </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> tcp string to send </td>
    </tr>
            <tr>
        <td> receive </td>
        <td> The new receive string for this monitor. </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> tcp string to receive </td>
    </tr>
            <tr>
        <td> probe_timeout </td>
        <td> The new timeout in which the system will timeout the monitor probe. </td>
        <td align=center> changed </td>
        <td align=center> int </td>
        <td align=center> 10 </td>
    </tr>
            <tr>
        <td> reverse </td>
        <td> The new value for whether the monitor operates in reverse mode. </td>
        <td align=center> changed </td>
        <td align=center> bool </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> transparent </td>
        <td> The new value for whether the monitor operates in transparent mode. </td>
        <td align=center> changed </td>
        <td align=center> bool </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> cipher_list </td>
        <td> The new value for the cipher list. </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> +3DES:+kEDH </td>
    </tr>
            <tr>
        <td> compatibility </td>
        <td> The new SSL compatibility setting. </td>
        <td align=center> changed </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> client_cert </td>
        <td> The new client cert setting. </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> /Common/default </td>
    </tr>
            <tr>
        <td> client_key </td>
        <td> The new client key setting. </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> /Common/default </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - For more information on using Ansible to manage F5 Networks devices see https://www.ansible.com/integrations/networks/f5.
    - Requires the f5-sdk Python package on the host. This is as easy as ``pip install f5-sdk``.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`/usage/support`


For help developing modules, should you be so inclined, please read :doc:`Getting Involved </development/getting-involved>`, :doc:`Writing a Module </development/writing-a-module>` and :doc:`Guidelines </development/guidelines>`.
.. The contents of this file are included in multiple topics.
.. This file should not be changed in a way that hinders its ability to appear in multiple documentation sets. 

The |chef server| server requires that every node that is under management by |chef| also have an accurate clock that is synchronized very closely with the clock on the |chef server|. If the clocks are not synchronized closely, the authentication process may fail when the clocks are out-of-sync by more than 15 minutes. A failure will trigger a ``401 Unauthorized`` response similar to: 

.. code-block:: bash

   [Tue, 01 Nov 2011 16:55:23 -0700] INFO: *** Chef 11.X.X ***
   [Tue, 01 Nov 2011 16:55:23 -0700] INFO: Client key /etc/chef/client.pem is not present - registering
   [Tue, 01 Nov 2011 16:55:24 -0700] INFO: HTTP Request Returned 401 Unauthorized: 
       Failed to authenticate as ORGANIZATION-validator. Synchronize the clock on your host.
   [Tue, 01 Nov 2011 16:55:24 -0700] FATAL: Stacktrace dumped to /var/chef/cache/chef-stacktrace.out
   [Tue, 01 Nov 2011 16:55:24 -0700] FATAL: Net::HTTPServerException: 401 "Unauthorized"

In this situation, re-synchronize the system clocks with the |ntp| server, and then re-run the |chef client|.
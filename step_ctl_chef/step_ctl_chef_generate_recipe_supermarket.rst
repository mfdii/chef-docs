.. This is an included how-to. 


The ``default.rb`` recipe is created when a cookbook is generated. A recipe is updated using a text editor. For example:

.. code-block:: ruby

   package 'apache2' # Installs the apache2 package
   
   service 'apache2' do
     action [:start, :enable] # Starts and enables the apache2 service on boot
   end
   
   template '/var/www/html/index.html' do
     source 'index.html.erb' # Template for /var/www/html/index.html
   end

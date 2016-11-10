# Solutions to problems using Magento 2.

* **Problem**: CSS files not being found.  
  **Solution**: Run the following command: `bin/magento setup:static-content:deploy`.  

* **Problem**: `Error: Cannot instantiate interface Magento\Framework\App\Config\Scope\ReaderPoolInterface` or similar message.  
  **Solution**: If you have not installed the Magento application yet, install it with `setup:install`. If the Magento application has been installed try clearing caches and `/var/generation` and `/var/di` directories. If you are making changes to php classes you will often need to clear the `/var/generation` directory in order for autogenerated files to be created.

* **Problem**: ```[Zend_Db_Statement_Exception] SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry '1' for key 'PRIMARY', query was: INSERT INTO `eav_entity_type` (`entity_type_code`, `entity_model`, `attribute_model`, `entity_table`, `value_table_prefix`, `entity_id_field`, `increment_model`, `increment_per_store`, `increment_pad_length`, `increment_pad_char`, `additional_attribute_table`, `entity_attribute_collection`, `entity_type_id`) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?)```  
  **Solution**: If this happens during installation of the Magento application, it may be because you are adding rows to eav_entity_type. Magento hard-codes the values of `entity_type_id` in the `eav_entity_type` table, so you cannot run any custom or third party Modules install scripts until all core Magento install scripts have run. I haven't found a good way to disable the modules during this step, so I temporarily changed the filenames of registration.php in each of my custom modules so they would not run.

* **Problem**: `[InvalidArgumentException] There are no commands defined in the "setup:static-content" namespace.` You will probably also see the list of bin/magento cli commands is much smaller than normal.
  **Solution**: You probably have not installed the Magento application yet, install it with `setup:install`.

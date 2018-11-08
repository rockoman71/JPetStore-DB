To Reset DB:

mysql -u root -e "DROP DATABASE jpetstore_sit"
mysql -u root -e "CREATE DATABASE jpetstore_sit"
mysql -u root -e "grant all privileges on jpetstore_sit.* to 'jpetstore'@'localhost'"

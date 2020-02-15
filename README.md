# docker-wordpress_modified
WordPress Docker image with some tweaks

1. can upload large files (~50MB)
2. writable /wp-content directory if it be mounted as Docker Volume (by `FS_METHOD` definition)
3. SMTP feature (msmtp)

To modify msmtp configuration, edit /var/www/msmtp.conf

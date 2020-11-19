# Busybox image that contains the simple 'httpd'
# https://git.busybox.net/busybox/tree/networking/httpd.c
FROM busybox

# Serve from this directory
WORKDIR /httpd

# Copy over the scripts
COPY script.sh index.cgi /httpd/cgi-bin/

# Start up busybox's httpd service, listen on port 8080 and
# stay in the foreground. Prints out verbose logs, too.
# See https://git.busybox.net/busybox/tree/networking/httpd.c for
# details
CMD [ "httpd", "-vv", "-p", "8080", "-f" ]

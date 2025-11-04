FROM alpine:3.19

# Add bash if needed
RUN apk add --no-cache bash

# Copy script into image
COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]

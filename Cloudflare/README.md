# Cloudflare Tunnel Readme

## Purpose
This Docker container is used to create a [Cloudflare Tunnel](https://developers.cloudflare.com/cloudflare-tunnel/) connection between your local machine and an Nginx server running a documentation site. The tunnel allows you to access the documentation site via a public IP address provided by Cloudflare, enhancing security and visibility.

## Prerequisites
- **Cloudflare Account**: You need a Cloudflare account and a working domain.
- **Nginx Server**: Ensure your Nginx server is hosting the documentation site and accessible on a specific port (e.g., 80).
- **DNS Setup**: Set up an A record for the domain you want to use with the Cloudflare Tunnel in the DNS settings.

## Steps to Deploy

1. **Prepare Your Environment**:
   - Ensure your Nginx server is running and accessible at `http://example.com` (or replace with your domain).
   - Create a `.env` file with your Cloudflare Tunnel token, formatted as follows:
     ```plaintext
     TUNNEL_TOKEN=your-tunnel-token-here
     ```

2. **Build the Docker Image**:
   Navigate to the directory containing your `docker-compose.yml` file and run the following command to build the Docker image:
     ```bash
     docker-compose build
     ```

3. **Start the Cloudflare Tunnel**:
   Use the following command to start the Cloudflare Tunnel service:
     ```bash
     docker-compose up -d
     ```

4. **Verify the Connection**:
   Check the logs for any errors and ensure the tunnel is running successfully by connecting to `https://your-domain.com`. You should be able to access your documentation site through this tunnel.

## Notes

- The Cloudflare Tunnel uses a unique IP address provided by Cloudflare, which allows you to securely connect to your Nginx server without exposing it directly on the public internet.
- Ensure that your `.env` file is not version-controlled and stored safely, as it contains sensitive information.

For more detailed instructions or troubleshooting, refer to the [official Cloudflare Tunnel documentation](https://developers.cloudflare.com/cloudflare-tunnel/).

## Conclusion

This Cloudflare Tunnel setup provides a secure and scalable way to access your documentation site while leveraging the power of Cloudflare for domain management and security. Happy documenting!
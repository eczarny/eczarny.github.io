# divisiblebyzero.com

## Testing

Tailwind CSS is used for styling and a local Node.js HTTP server is used for testing. A [Dev Container](https://code.visualstudio.com/docs/devcontainers/containers) is used for development and all requisite npm packages should be installed.

To run the development environment:

    npm run dev

You can now navigate to http://localhost:8080 for testing.

To test on an external device first make sure `route_localnet` is enabled:

    sudo sysctl -w net.ipv4.conf.wlo1.route_localnet=1

Now you can add an `iptables` rule to route traffic to the host to the container:

    sudo iptables -v -t nat -I PREROUTING -i wlo1 -p tcp --dport 8080 -j DNAT --to-destination 127.0.0.1:8080

These changes are ephemeral so they need to be executed every time prior to testing.

## Building

To build for distribution:

    npm run dist

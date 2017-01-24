# PlugChatterboxExample

An example application for using [plug_chatterbox](https://github.com/potatosalad/plug_chatterbox).

## Running

 * `git clone git@gitgub.com:potatosalad/plug_chatterbox_example.git`
 * `cd plug_chatterbox_example`
 * An SSL certificate is required as most browsers only support
   HTTP/2 when using HTTPS
 * `openssl req -new -newkey rsa:4096 -days 365 -nodes -x509
    -subj "/C=US/ST=Denial/L=Springfield/O=Dis/CN=www.example.com"
    -keyout priv/server.key -out priv/server.pem`
 * `mix deps.get`
 * `iex -S mix`
 * In another terminal, run one of the following:
   * Clear proxy: `nghttpx -f'*,4003;no-tls' -b'127.0.0.1,4002;;proto=h2'`
   * TLS proxy: `nghttpx -f'*,4003;tls' -b'127.0.0.1,4002;;proto=h2' priv/server.key priv/server.pem`
 * Navigate to (Clear) [http://localhost:4003](http://localhost:4003) or (TLS) [https://localhost:4003](https://localhost:4003)

Most browsers don't support the "prior knowledge" method of HTTP/2 connection establishment, which is why using a HTTP/1.1 upgrade to HTTP/2 proxy is necessary to see the page:

![http2](https://raw.githubusercontent.com/potatosalad/plug_chatterbox_example/master/docs/screenshot.png)

# VPN-
A lightweight VPN implemented in Java using RSA, AES, and X.509 certificates. Includes a secure handshake, mutual authentication, and encrypted TCP port forwarding. Certificates are managed with OpenSSL, making it a practical project to learn secure communication.

🚀 Features

• Secure handshake protocol with mutual authentication.

• RSA + AES (CTR mode) hybrid encryption.

• X.509 certificates signed by a Certificate Authority (CA).

• Transparent TCP port forwarding (any TCP service can use the VPN).

• Certificate and key management using OpenSSL.


📂 Project Structure

/src
  ├── server/ForwardServer.java
  ├── client/ForwardClient.java
  └── communication/handshake/...
/certs
  ├── CA.pem
  ├── server.pem
  ├── client.pem
  └── keys...


⚙️ Setup

1. Compile
javac -d out -cp src src/**/*.java

2. Run Server
java -cp out server.ForwardServer \
  --handshakeport=2206 \
  --usercert=certs/server.pem \
  --cacert=certs/CA.pem \
  --key=certs/serverprivatekey.pem

3. Run Client
java -cp out client.ForwardClient \
  --handshakehost=localhost \
  --handshakeport=2206 \
  --targethost=localhost \
  --targetport=1337 \
  --usercert=certs/client.pem \
  --cacert=certs/CA.pem \
  --key=certs/clientprivatekey.der


Architecture

<img width="1536" height="1024" alt="Architecture" src="https://github.com/user-attachments/assets/c81790af-7912-4839-928a-e137fe8d399d" />


🔑 Certificates

Generate certificates using OpenSSL:

• Create a CA.

• Generate client & server key pairs.

• Sign certificates with the CA.

• Place them inside the certs/ folder.


🛠️ Technologies

• Java (JDK 17+)
• OpenSSL for certificate management
• RSA, AES, X.509 for security


📜 License

Released under the MIT License


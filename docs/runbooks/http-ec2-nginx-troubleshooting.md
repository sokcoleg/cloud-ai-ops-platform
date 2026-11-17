# EC2 Nginx HTTP Troubleshooting

## Purpose

This runbook describes how to troubleshoot an EC2 instance when the Nginx web server is not reachable over HTTP.

## 1. Check the Nginx service

```bash
sudo systemctl status nginx
```

Checks whether the Nginx service is running.

Expected result:

```text
active (running)
```

## 2. Check port 80

```bash
sudo ss -lntp | grep :80
```

Checks whether Nginx is listening on TCP port 80.

Expected result:

```text
0.0.0.0:80
```

## 3. Test Nginx locally

```bash
curl localhost
```

Sends an HTTP request directly to Nginx from the EC2 instance.

If this works, Nginx and the local Linux network stack are working correctly.

## 4. Check the Security Group

Verify that inbound HTTP traffic is allowed:

```text
Protocol: TCP
Port: 80
Source: 0.0.0.0/0
```

## 5. Check the Route Table

Verify that the public subnet has a route to an Internet Gateway:

```text
0.0.0.0/0 → Internet Gateway
```

## 6. Check the Public IPv4 address

Confirm that the EC2 instance has a current public IPv4 address.

Test it in a browser:

```text
http://PUBLIC_IP
```

Do not use HTTPS unless port 443 and TLS are configured.

## Result

Nginx, TCP port 80, local HTTP connectivity, Security Group rules, routing, and public access were verified successfully.

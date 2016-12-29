# knuckle
A small script for automating encrypted tunnels on OS X

## What is this?

`knuckle` is a script that encrypts internet traffic through a SOCKS5 proxy. 

It works by tunnelling traffic through an SSH connection on a proxy server. 

## How do I use it?

Simply run `$ sudo knuckle` to begin your session, then hit ENTER to close your session.

If you use AnyBar, knuckle will turn the status indicator blue for the duration of your session.

## How does it work?

Really `knuckle` is a glorified wrapper around the following command:

`ssh -Nn -D 8085 -l $user $ip`

This opens up a tunnel to $ip that SOCKS5-compatible programs (e.g. web brosers) send their traffic to.

`knuckle` automates the creation of the proxy instance, the establishment of the tunnel, the creation of the SOCKS proxy, and all subsequent breakdown upon completion.

`knuckle` stays alive for the duration of your session. When you interrupt it, `knuckle` will unset the proxy, close the tunnel, and shut down the proxy instance.

## Why would I want to use knuckle?

`knuckle` is intended for cases where a user would want to have a short session on an untrusted network (e.g. browsing while on public wifi). `knuckle` automates the different pieces throughout that workflow.

## Why not use a VPN?

If you have a legitimate VPN to connect to, you should use that instead. This script is for short sessions from programs that are capable of using SOCKS proxies (e.g. any modern web browser).

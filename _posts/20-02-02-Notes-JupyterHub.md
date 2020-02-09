---
title: Notes JupyterHub
layout: post
tags: jupyter,jupyterlab,notebooks,ipython,server,jupyterhub
---

## Installation

There are some prepared ways to install JupyterHub on the own server. One of them is for a simple minimal setup, designed to be fast forward configurable and for a small base of users with limited performance. If this fits for you check it out:

https://tljh.jupyter.org/en/latest/install/index.html

Others are designed to be used in more complex setups. In my case I want to install it my own way, to integrate it best into my setup along the [Install JupyterHub from the ground up](https://jupyterhub.readthedocs.io/en/stable/installation-guide-hard.html) guide.

The server should be reachable under the subdomain `jupyter.domain.tld` , which can be archieved by binding the url to a specific port and use a reverse proxy in apache directing the subdomain to this port. https://jupyterhub.readthedocs.io/en/stable/reference/config-proxy.html

When it comes to changing the config in the tutorial just add:

```python
c.JupyterHub.bind_url = 'http://127.0.0.1:8007'
```

used port 8007 instead of default 8000 because its already in use.

Added `proxy_http`, `proxy_wstunnel` to apache modules in plesk interface (ssl is always enabled)


# ooblic

<div align="center"><img src="logo.svg"/></div>

OOBLIC use [interactsh](https://github.com/projectdiscovery/interactsh)
- when we use interactsh-client sometimes domains sends back respone from internal ip insted of proxy ip making it confusing to work with. ooblic solves this issue
- i learned interactsh can be used as a library from [here](https://github.com/projectdiscovery/interactsh/blob/main/examples/client.go) and buid ooblic

### ISSUE
```yaml
# terminal 1
┌──(loca㉿loca)-[~]
└─$ interactsh-client

    _       __                       __       __  
   (_)___  / /____  _________ ______/ /______/ /_ 
  / / __ \/ __/ _ \/ ___/ __ '/ ___/ __/ ___/ __ \
 / / / / / /_/  __/ /  / /_/ / /__/ /_(__  ) / / /
/_/_/ /_/\__/\___/_/   \__,_/\___/\__/____/_/ /_/

		projectdiscovery.io

[INF] Current interactsh version 1.2.4 (latest)
[INF] Listing 1 payload for OOB Testing
[INF] d1h2c8kubu2319mvfgm0waow9srzinyu8.oast.me
[d1h2c8kubu2319mvfgm0waow9srzinyu8] Received DNS interaction (AAAA) from 59.144.144.6 at 2025-06-30 05:55:37
[d1h2c8kubu2319mvfgm0waow9srzinyu8] Received HTTP interaction from 106.215.144.126 at 2025-06-30 05:55:37
[d1h2c8kubu2319mvfgm0waow9srzinyu8] Received DNS interaction (A) from 59.144.144.6 at 2025-06-30 05:56:33
```
```yaml
# terminal 2
┌──(loca㉿loca)-[~]
└─$ cat scope.txt | httpx -H "Host d1h2c8kubu2319mvfgm0waow9srzinyu8.oast.me"
```
### SOLUTION
```yaml
┌──(loca㉿loca)-[~]
└─$ ooblic
             _     _ _      
  ___   ___ | |__ | (_) ___ 
 / _ \ / _ \| '_ \| | |/ __|
| (_) | (_) | |_) | | | (__ 
 \___/ \___/|_.__/|_|_|\___| v1.0.0

[INF] d1h2c8kubu2319mvfgm0waow9srzinyu8.oast.me

[INF][DNS] example.com

[d1h2c8kubu2319mvfgm0waow9srzinyu8] Received DNS interaction (A) from 59.144.144.6 at 2025-06-30 05:55:27
[d1h2c8kubu2319mvfgm0waow9srzinyu8] Received DNS interaction (A) from 59.144.144.6 at 2025-06-30 05:55:27
[D1H2c8kUbu2319MVfGM0WAOW9SRZINyU8] Received DNS interaction (A) from 61.95.255.74 at 2025-06-30 05:55:27
[d1h2c8kubu2319mvfgm0waow9srzinyu8] Received DNS interaction (AAAA) from 59.144.144.6 at 2025-06-30 05:55:27
[d1h2c8kubu2319mvfgm0waow9srzinyu8] Received DNS interaction (AAAA) from 59.144.144.6 at 2025-06-30 05:55:27
[d1H2C8kUbU2319mvfgM0wAOW9SrziNYU8] Received DNS interaction (AAAA) from 61.95.255.74 at 2025-06-30 05:55:27

[INF][DNS] example2.in

[d1h2c8kubu2319mvfgm0waow9srzinyu8] Received DNS interaction (A) from 59.144.144.6 at 2025-06-30 05:56:33
[d1h2c8kubu2319mvfgm0waow9srzinyu8] Received DNS interaction (AAAA) from 59.144.144.6 at 2025-06-30 05:56:33
[d1h2c8kubu2319mvfgm0waow9srzinyu8] Received DNS interaction (AAAA) from 59.144.144.6 at 2025-06-30 05:56:33
[d1h2c8kubu2319mvfgm0waow9srzinyu8] Received HTTP interaction from 106.215.144.126 at 2025-06-30 05:56:33
[d1h2c8kubu2319mvfgm0waow9srzinyu8] Received DNS interaction (AAAA) from 59.144.144.6 at 2025-06-30 05:56:41
[d1H2c8KubU2319MVFGm0waOw9sRzInYu8] Received DNS interaction (A) from 61.95.255.74 at 2025-06-30 05:56:41
[d1H2c8kUbu2319mvFGM0wAoW9srzinYu8] Received DNS interaction (AAAA) from 61.95.255.74 at 2025-06-30 05:56:41
[D1H2C8kUBU2319mVFGm0wAow9srziNYU8] Received DNS interaction (AAAA) from 61.95.255.74 at 2025-06-30 05:56:41

[INF][HTTP] example3.com

[d1h2c8kubu2319mvfgm0waow9srzinyu8] Received HTTP interaction from 106.215.144.126 at 2025-06-30 05:56:41
```

### Usage

```
ooblic -d example.com -H "Host: d1h2c8kubu2319mvfgm0waow9srzinyu8.oast.me"
```

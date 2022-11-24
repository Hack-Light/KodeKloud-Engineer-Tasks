# TASK

During the daily standup, it was pointed out that the timezone across Nautilus Application Servers in Stratos Datacenter doesn't match with that of the local datacenter's timezone, which is `America/Martinique`.

Correct the mismatch.

# SOLUTION

App server 1

```bash
# ssh into the first server
ssh tony@172.16.238.10

# change the timezone to America/Martinique
sudo timedatectl set-timezone America/Martinique

# confirm timezone
timedatectl

# sample output

      Local time: Sun 2022-10-30 17:56:16 AST
  Universal time: Sun 2022-10-30 21:56:16 UTC
        RTC time: n/a
       Time zone: America/Martinique (AST, -0400)
     NTP enabled: n/a
NTP synchronized: yes
 RTC in local TZ: no
      DST active: n/a
```

App server 2

```bash
# ssh into the second server
ssh steve@172.16.238.11

# confirm current timezone
timedatectl

# sample output

      Local time: Sun 2022-10-30 21:57:58 UTC
  Universal time: Sun 2022-10-30 21:57:58 UTC
        RTC time: n/a
       Time zone: UTC (UTC, +0000)
     NTP enabled: n/a
NTP synchronized: yes
 RTC in local TZ: no
      DST active: n/a


# change the timezone to America/Martinique
sudo timedatectl set-timezone America/Martinique

# confirm timezone
timedatectl

# sample output

      Local time: Sun 2022-10-30 17:56:16 AST
  Universal time: Sun 2022-10-30 21:56:16 UTC
        RTC time: n/a
       Time zone: America/Martinique (AST, -0400)
     NTP enabled: n/a
NTP synchronized: yes
 RTC in local TZ: no
      DST active: n/a
```

App server 3

```bash
# ssh into the third server
ssh banner@172.16.238.12

# change the timezone to America/Martinique
sudo timedatectl set-timezone America/Martinique

# confirm timezone
timedatectl

# sample output

      Local time: Sun 2022-10-30 17:56:16 AST
  Universal time: Sun 2022-10-30 21:56:16 UTC
        RTC time: n/a
       Time zone: America/Martinique (AST, -0400)
     NTP enabled: n/a
NTP synchronized: yes
 RTC in local TZ: no
      DST active: n/a
```

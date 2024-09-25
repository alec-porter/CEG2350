## Lab 08

- Name: Alec Porter
- Email: porter.223@wright.edu

## Part 1 - Game the system

- Game name: bastet
- How to install: sudo apt install bastet
- Location of game executable: /usr/games/bastet
- How to run game: type 'bastet' at the prompt

## Part 2 - Process Control

1. `ps` field descriptions:
   - USER / UID: effective user id
   - PID: a number representing the process id
   - PPID: parent process id
   - TTY: controlling terminal for the process
   - STAT: process state represented by various codes
   - COMMAND / CMD: command with arguments as strings
2. `ps` command: ps -xo uid,pid,ppid,tty,stat,cmd (the -x flag will list all user own processes including ones without a controlling terminal)
3. Output of `ps` with two shells, one running the game:
```
pidof bastet
9163

ps -p 9163 -o pid,ppid,cmd
    PID    PPID CMD
   9163    8983 bastet

ps -p 8983
    PID TTY          TIME CMD
   8983 pts/0    00:00:00 bash

ps -xo uid,pid,ppid,tty,stat,cmd
  UID     PID    PPID TT       STAT CMD
 1000    2170       1 ?        Ss   /lib/systemd/systemd --user
 1000    2171    2170 ?        S    (sd-pam)
 1000    2180    2170 ?        S<sl /usr/bin/pipewire
 1000    2184    2170 ?        S<sl /usr/bin/wireplumber
 1000    2186    2170 ?        S<sl /usr/bin/pipewire-pulse
 1000    2187    2170 ?        SNs  /usr/bin/dbus-broker-launch --scope user
 1000    2189       1 ?        SNl  /usr/bin/gnome-keyring-daemon --daemonize --login
 1000    2195    2187 ?        S    dbus-broker --log 4 --controller 10 --machine-id 5aa82f6af
 1000    2202    2170 ?        SNsl /usr/libexec/gvfsd
 1000    2212    2170 ?        SNl  /usr/libexec/gvfsd-fuse /run/user/1000/gvfs -f
 1000    2222    2170 ?        SNsl /usr/libexec/tracker-miner-fs-3
 1000    2232    2170 ?        SNsl /usr/libexec/gvfs-udisks2-volume-monitor
 1000    2237    2170 ?        SNsl /usr/libexec/gvfs-mtp-volume-monitor
 1000    2244    2170 ?        SNsl /usr/libexec/gvfs-afc-volume-monitor
 1000    2249    2170 ?        SNsl /usr/libexec/gvfs-goa-volume-monitor
 1000    2253    2170 ?        SNsl /usr/libexec/goa-daemon
 1000    2255    2152 tty2     SNsl+ /usr/libexec/gdm-x-session --run-script env GNOME_SHELL_S
 1000    2257    2255 tty2     S<l+ /usr/lib/xorg/Xorg vt2 -displayfd 3 -auth /run/user/1000/g
 1000    2263    2170 ?        SNsl /usr/libexec/goa-identity-service
 1000    2265    2170 ?        SNsl /usr/libexec/gvfs-gphoto2-volume-monitor
 1000    2310    2255 tty2     SNl+ /usr/libexec/gnome-session-binary --session=pop
 1000    2369    2170 ?        SNsl /usr/libexec/at-spi-bus-launcher
 1000    2374    2369 ?        SN   /usr/bin/dbus-broker-launch --config-file=/usr/share/defau
 1000    2375    2374 ?        S    dbus-broker --log 4 --controller 9 --machine-id 5aa82f6aff
 1000    2392    2170 ?        SNsl /usr/libexec/gnome-session-ctl --monitor
 1000    2404    2170 ?        SNsl /usr/libexec/gnome-session-binary --systemd-service --sess
 1000    2427    2170 ?        S<sl /usr/bin/gnome-shell
 1000    2461    2170 ?        SNsl /usr/libexec/xdg-permission-store
 1000    2466    2170 ?        SNsl /usr/libexec/gnome-shell-calendar-server
 1000    2474    2170 ?        SNsl /usr/libexec/evolution-source-registry
 1000    2481    2170 ?        SNsl /usr/libexec/evolution-calendar-factory
 1000    2493    2170 ?        SNsl /usr/libexec/dconf-service
 1000    2494    2170 ?        SNsl /usr/libexec/evolution-addressbook-factory
 1000    2502    2202 ?        SNl  /usr/libexec/gvfsd-trash --spawner :1.9 /org/gtk/gvfs/exec
 1000    2517    2170 ?        SNsl /usr/libexec/xdg-desktop-portal
 1000    2521    2170 ?        SNsl /usr/libexec/xdg-document-portal
 1000    2529    2170 ?        SNsl /usr/libexec/xdg-desktop-portal-gnome
 1000    2558    2170 ?        SNsl /usr/bin/gjs /usr/share/gnome-shell/org.gnome.Shell.Notifi
 1000    2561    2170 ?        SNsl /usr/libexec/at-spi2-registryd --use-gnome-session
 1000    2576    2170 ?        SNs  sh -c /usr/bin/ibus-daemon --panel disable $([ "$XDG_SESSI
 1000    2577    2170 ?        SNsl /usr/libexec/gsd-a11y-settings
 1000    2579    2170 ?        SNsl /usr/libexec/gsd-color
 1000    2580    2576 ?        SNl  /usr/bin/ibus-daemon --panel disable --xim
 1000    2581    2170 ?        SNsl /usr/libexec/gsd-datetime
 1000    2583    2170 ?        SNsl /usr/libexec/gsd-housekeeping
 1000    2585    2170 ?        SNsl /usr/libexec/gsd-keyboard
 1000    2587    2404 ?        SNl  /usr/libexec/evolution-data-server/evolution-alarm-notify
 1000    2588    2170 ?        SNsl /usr/libexec/gsd-media-keys
 1000    2594    2170 ?        SNsl /usr/libexec/gsd-power
 1000    2597    2170 ?        SNsl /usr/libexec/gsd-print-notifications
 1000    2598    2170 ?        SNsl /usr/libexec/gsd-rfkill
 1000    2601    2170 ?        SNsl /usr/libexec/gsd-screensaver-proxy
 1000    2604    2170 ?        SNsl /usr/libexec/gsd-sharing
 1000    2608    2170 ?        SNsl /usr/libexec/gsd-smartcard
 1000    2613    2404 ?        SNl  /usr/libexec/gsd-disk-utility-notify
 1000    2614    2170 ?        SNsl /usr/libexec/gsd-sound
 1000    2618    2170 ?        SNsl /usr/libexec/gsd-wacom
 1000    2622    2170 ?        SNsl /usr/libexec/gsd-xsettings
 1000    2631    2404 ?        SNl  touchegg
 1000    2641    2404 ?        SNl  /usr/bin/python3 /usr/lib/hidpi-daemon/hidpi-notification
 1000    2645    2580 ?        SNl  /usr/libexec/ibus-dconf
 1000    2646    2580 ?        SNl  /usr/libexec/ibus-extension-gtk3
 1000    2648    2170 ?        SNl  /usr/libexec/ibus-x11 --kill-daemon
 1000    2656    2404 ?        SNl  /usr/bin/python3 /usr/lib/hidpi-daemon/hidpi-daemon
 1000    2661    2170 ?        SNsl /usr/libexec/ibus-portal
 1000    2702    2170 ?        SNl  /usr/libexec/gsd-printer
 1000    2766    2170 ?        SNsl /usr/bin/gjs /usr/share/gnome-shell/org.gnome.ScreenSaver
 1000    2782    2580 ?        SNl  /usr/libexec/ibus-engine-simple
 1000    2794    2170 ?        SNsl /usr/libexec/xdg-desktop-portal-gtk
 1000    2839    2427 ?        SNl  gjs /usr/share/gnome-shell/extensions/ding@rastersoft.com/
 1000    2857    2170 ?        SNsl /usr/libexec/gvfsd-metadata
 1000    2871    2170 ?        SNsl /usr/bin/pop-system-updater
 1000    3878    2404 ?        SNl  io.elementary.appcenter -s
 1000    4032    2427 ?        SNl  firefox
 1000    4119    4032 ?        SNl  /usr/lib/firefox/firefox-bin -contentproc -parentBuildID 2
 1000    4141    4032 ?        SNl  /usr/lib/firefox/firefox-bin -contentproc -childID 1 -isFo
 1000    4197    4032 ?        SNl  /usr/lib/firefox/firefox-bin -contentproc -childID 2 -isFo
 1000    4247    4032 ?        SNl  /usr/lib/firefox/firefox-bin -contentproc -parentBuildID 2
 1000    4436    4032 ?        SNl  /usr/lib/firefox/firefox-bin -contentproc -childID 9 -isFo
 1000    4707    2189 ?        SN   /usr/bin/ssh-agent -D -a /run/user/1000/keyring/.ssh
 1000    5044    4032 ?        SNl  /usr/lib/firefox/firefox-bin -contentproc -parentBuildID 2
 1000    6960    4032 ?        SNl  /usr/lib/firefox/firefox-bin -contentproc -childID 35 -isF
 1000    8815    4032 ?        SNl  /usr/lib/firefox/firefox-bin -contentproc -childID 65 -isF
 1000    8879    4032 ?        SNl  /usr/lib/firefox/firefox-bin -contentproc -childID 66 -isF
 1000    8917    4032 ?        SNl  /usr/lib/firefox/firefox-bin -contentproc -childID 67 -isF
 1000    8957    2170 ?        Ssl  /usr/libexec/gnome-terminal-server
 1000    8983    8957 pts/0    Ss   bash
 1000    9080    8957 pts/3    Ss   bash
 1000    9163    8983 pts/0    S+   bastet
 1000    9183    8957 pts/1    Ss   bash
 1000    9194    9183 pts/1    SN+  vim lab08.md
 1000    9209    9080 pts/3    R+   ps -xo uid,pid,ppid,tty,stat,cmd
```
4. For the game:
   - Process id: 9163
   - Parent process id: 8983
   - What is the parent process: bash
5. `kill` to kill only the game: kill 9163  or  pkill bastet
   - Describe what the effect was: the process ended in the other terminal and went back to the prompt
6. `kill` to kill the game and it's parent process: kill -kill 8983
   - Describe what the effect was: the terminal and shell closed killing any child processes with it
7. Describe what happens if you close / `exit` your connection with Shell C and determine if you can reenter the game (resume the process).
   - Answer: Closing a single shell only effects the game running in that specific shell.  If games are running in other shells they will continue to run.  You can open multiple shells each running the game and kill any number of games without impacting the other games.  

## Part 3 - back and fore

1. Run in the foreground: bastet
2. `STOP` signal to suspend it: kill -19 5424
3. Proof of life from `ps` output: ps 5424
```
    PID TTY      STAT   TIME COMMAND
   5424 pts/1    T      0:00 bastet

```
4. Resume in the foreground: fg
5. `TERMINATE` signal to kill it: kill -9 5424
6. Start as a background process: bastet &
7. Output of `jobs` from controlling terminal:
```
[1]   Stopped                 bastet
[2]-  Stopped                 bastet
[3]+  Stopped                 bastet
```
Output of `ps`: ps -xo uid,pid,ppid,tty,stat,cmd | grep bastet
```
 1000    5674    4957 pts/1    TN   bastet
 1000    5675    4957 pts/1    TN   bastet
 1000    5676    4957 pts/1    TN   bastet
```
8. Kill job: kill -9 5674
9. Move job to the foreground: fg %2 
10. Describe what happens, using process knowledge in your description, if you close / `exit` your connection with this shell and determine if you can reenter the game (resume the process).
   - Answer: Becasue I ran all three games in a single shell, if I exit that shell I will kill all of the game processes because they are children processes to the shell. 

## Part 4 - Detach

1. Create a `tmux` session: sudo apt install tmux -y; tmux; bastet
2. Detach from the session: 'ctrl'+'b' then 'd'
```
[detached (from session 0)]
```
3. `ps` command: ps -xo uid,pid,ppid,tty,stat,cmd | grep bastet
```
1000    7852    7838 pts/2    SN+  bastet
```
4. Command to list `tmux` sessions: tmux ls
```
0: 1 windows (created Tue Mar 19 15:56:53 2024)
```
5. How can you determine if your `tmux` session with your game running is available?
   - Answer: There are a variety of ways: you can use ps to see if tmux is running, you can see what tmux sessions are running with 'tmux ls', when you create a new tmux session you can name it something unique like 'tmux new -s game' so it is easier to idetify with 'tmux ls'
7. Reattach to `tmux` session: tmux attach (if running a single session); tmux attach -t 0 (when you need to identify what session to reattach when multiple detached sessions are running)
8. Kill `tmux` session: 'ctrl'+'b' then '&' then 'y'

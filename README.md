
# Born2BeRoot

*This project was created as part of the 42 curriculum by `<katakaha>`.*

<details>
<summary>🌐 English README</summary>

## Description

Born2BeRoot is a project of making your own virtual machine and installing a simple server with basic safety features. You must partition the drive at least 2 encrypted partitions using LVM. You have the option of choosing Debian or Rocky as the OS. You must add a firewall, SSH, a strong password policy, sudo, and a script file that displays some specified information on all terminals every 10 minutes.

## Instructions

Open VirtualBox and and press "Start" for katakaha's VM. Once inside, unlock the disk with password: 12345678aA. After you unlock the disk, you can access the VM's terminal via "ssh" from your localhost's terminal. You do this by entering: `ssh katakaha@localhost -p 4242`. It will ask you for a password which is: 1qwertyuiopZ. You can access a different user by changing the katakaha@localhost to the user of your choice. You change between users with the `su` command.
Check the signature by `shasum "katakaha_s VM.vdi"`. It is located at `/sgoinfre/b2br - vm/katakaha_s VM/`. You can compare with `cat ~/(path)/signature.txt`

Below I have prepared a set of useful commands to check the needed criteria of the review.
<table>
	<thead>
		<tr>
			<th>Category</th>
			<th>Command</th>
			<th>What it shows / does</th>
			<th>Did use?</th>
		</tr>
	</thead>
	<tbody>
		<!-- System and authentication -->
		<tr>
			<td>System</td>
			<td><code>uname -a</code></td>
			<td>Kernel name and version</td>
		</tr>
		<tr>
			<td></td>
			<td><code>hostnamectl</code></td>
			<td>Hostname and OS info</td>
			<td>✅</td>
		</tr>
		<tr>
			<td></td>
			<td><code>sudo hostnamectl set-hostname [new name]</code> or <code>sudo visudo</code> which opens /etc/hostname</td>
			<td>Change hostname and don't forget to change the ip hostname, as well</td>
			<td>✅</td>
		</tr>
		<tr>
			<td></td>
			<td><code>sudo nano /etc/hosts</code> and change ip name to your new name</td>
			<td>Change IP hostname</td>
			<td>✅</td>
		</tr>
		<tr>
			<td></td>
			<td><code>whoami</code></td>
			<td>Current user</td>
		</tr>
		<<tr>
			<td></td>
			<td><code>sudo -l</code></td>
			<td>Show allowed sudo commands in the visudo file</td>
		</tr>
		<tr>
			<td></td>
			<td><code>getent passwd [user]</code></td>
			<td>Check if user exists</td>
		</tr>
		<tr>
			<td></td>
			<td><code>getent passwd [group]</code></td>
			<td>Check if group exist</td>
		</tr>
		<tr>
			<td></td>
			<td><code>id</code></td>
			<td>UID, GID, groups</td>
		</tr>
		<!-- Users & groups -->
		<tr>
			<td>Users/Groups</td>
			<td><code>sudo adduser [user]</code></td>
			<td>Create user</td>
			<td>✅</td>
		</tr>
		<tr>
			<td></td>
			<td><code>sudo deluser [user]</code></td>
			<td>Delete user</td>
		</tr>
		<tr>
			<td></td>
			<td><code>sudo addgroup [group]</code></td>
			<td>Create group</td>
		</tr>
		<tr>
			<td></td>
			<td><code>sudo delgroup [group]</code></td>
			<td>Delete group</td>
		</tr>
		<tr>
			<td></td>
			<td><code>sudo usermod -aG [group] [user]</code></td>
			<td>Add user to group</td>
		</tr>
		<tr>
			<td></td>
			<td><code>groups [user]</code></td>
			<td>Shows user's groups</td>
		</tr>
		<tr>
			<td></td>
			<td><code>sudo passwd [user]</code></td>
			<td>Change a user's password</td>
		</tr>
		<!-- Package, services, and firewall -->
		<tr>
			<td>Package/Services/Firewall</td>
			<td><code>dpkg -l | grep [pkg]</code></td>
			<td>Check if package is installed</td>
		</tr>
		<tr>
			<td></td>
			<td><code>systemctl status [service]</code></td>
			<td>Check service status</td>
			<td>✅</td>
		</tr>
		<tr>
			<td></td>
			<td><code>sudo systemctl is-enabled [service]</code></td>
			<td>Check if enabled at boot</td>
		</tr>
		<tr>
			<td></td>
			<td><code>sudo systemctl [start,stop,restart] [service]</code></td>
			<td>Manage service</td>
		</tr>
		<tr>
			<td></td>
			<td><code>sudo ufw status verbose</code></td>
			<td>Show firewall rules</td>
			<td>✅</td>
		</tr>
		<tr>
			<td></td>
			<td><code>sudo ufw allow [port]</code></td>
			<td>Allow port [number]</td>
		</tr>
		<!-- SSH & network-->
		<tr>
			<td>SSH/Network</td>
			<td><code>ss -tnlp | grep ssh</code> or <code>ss -tuln</code></td>
			<td>Check for listening ports</td>
		</tr>
		<tr>
			<td></td>
			<td><code>sudo systemctl status ssh</code></td>
			<td>Check SSH</td>
		</tr>
		<tr>
			<td></td>
			<td><code>ip a</code></td>
			<td>Show IP address</td>
		</tr>
		<tr>
			<td></td>
			<td><code>hostnamectl -l</code></td>
			<td>Show IP[short version]</td>
		</tr>
		<tr>
			<td></td>
			<td><code>ssh [username]@[IP] -p [port number]</code></td>
			<td>Connect with ssh</td>
		</tr>
		<!-- Disk, LVM, and partitions -->
		<tr>
			<td>LVM/Disk/Partitions</td>
			<td><code>lsblk</code></td>
			<td>Show block devices and mount points</td>
			<td>✅</td>
		</tr>
		<tr>
			<td></td>
			<td><code>df -h</code></td>
			<td>Disk usage by filesystem</td>
		</tr>
		<!-- Logs & sudo config -->
		<tr>
			<td>Sudo/Logs</td>
			<td><code>sudo visudo</code></td>
			<td>Edit sudoers safely</td>
		</tr>
		<tr>
			<td></td>
			<td><code>sudo cat /etc/sudoers</code></td>
			<td>view sudoers</td>
		</tr>
		<tr>
			<td></td>
			<td><code>sudo cat /etc/sudoer.d/[file]</code></td>
			<td>View custom sudo config</td>
		</tr>
		<tr>
			<td></td>
			<td><code>journalctl -xe</code></td>
			<td>Recent system logs</td>
		</tr>
		<tr>
			<td></td>
			<td><code>sudo tail -n 50 /var/log/auth.log</code></td>
			<td>Auth/sudo logs</td>
		</tr>
		<!-- Cron & monitoring script -->
		<tr>
			<td>Cron/monitoring.sh</td>
			<td><code>crontab -l</code></td>
			<td>Show current user crontab</td>
		</tr>
		<tr>
			<td></td>
			<td><code>sudo crontab -l</code></td>
			<td>Show root crontab</td>
		</tr>
		<tr>
			<td></td>
			<td><code>systemctl list-timers</code></td>
			<td>List timers</td>
		</tr>
		<tr>
			<td></td>
			<td><code>bash monitoring.sh</code></td>
			<td>Run script manually</td>
		</tr>
		<!-- Policies -->
		<tr>
			<td>Policies</td>
			<td><code>sudo nano /etc/pam.d/common-password</code></td>
			<td>Check password policies for setting a password</td>
			<td>✅</td>
		</tr>
		<tr>
			<td></td>
			<td><code>chage -l [user]</code></td>
			<td>Show password policy for user</td>
			<td>✅</td>
		</tr>
	</tbody>
</table>

## Resources

I got the general gist of how do to this project for this site. It gave me the starting steps of setting everything up. [Baigalmaa Baatar](https://baigal.medium.com/born2beroot-e6e26dfb50ac)<br>
I prepared for the review with the help from this site. It talks about each part from a defensive standpoint. [jizo](https://note.com/jizo_ts/n/nc3c228912a7b)

#### Other resources include:

- [Password Policy Options](https://manpages.debian.org/testing/libpam-pwquality/pam_pwquality.8.en.html)

- [Useful UFW commands](https://qiita.com/JhonnyBravo/items/f67d34c0ed8f2961919e)

- [Systemctl Command](https://qiita.com/sinsengumi/items/24d726ec6c761fc75cc9)

#### Using AI to better understand:

- What this project teaches

- What each part does

- Where to look for information

## Project Description

This project builds a virtual machine from scratch using a hypervisor and customizes settings with only the CLI. I configured:
- Security Policies - SSH access, AppArmor for application confinement, and UFW for the firewall.
- User mangement - Sudo for admin rights with strict password policies.
- Partitioning - LVM for root filesystem and swap space.
- Services Installed - sudo, openssh-server, ufw, libpam-pwquality, 
- Monitoring - custom script with cron for regular system status report.

### OS

I chose Debian over Rocky because Rocky is for enterprises and focuses on RHEL's policies. Debian has great stability, is community based, and provides many package resources which are easy to install. There is much information on troubleshooting as Debian is the base for many famous Linux distributions.

	Rocky: Great for servers with enterprise-class long-term support. Its standard security policy is more robust than Debian's, making it ideal for mission-critical environments. It's the successor to CentOS, so transitioning is smooth. Good to use if you are familiar with RHEL environments.

	Rocky Linux demerits: Slow software updates due to its focus on stability often leave packages outdated. It has a smaller, less mature community with limited documentation and uncertain long-term viability. It performs poorly for desktops due to compatibility issues and lacks full RHEL enterprise tools without paid add-ons.

	Debian: Open source OS that prioritizes software that conforms to the DFSG(Debian Free Software Guidelines). It focuses on stability and security, making it predictable and reliable. Instead of constantly updating to new, buggy versions, Debian adds security patches to old reliable software, minimizing attack surface. It goes through rigorous, slow, steady testing, making it very durable and stable.

	Debian demerits: Its stable branch ships very old software versions due to slow production focused on stability, forcing users needing recent features or hardware support to rely on unstable branches. Configuration can be complicated for beginners. Major releases are infrequent, so you cannot rely on new updates arriving promptly.

### Security System

Debian uses AppArmor for security, and I have it enabled in my virtual machine. MAC's mandatory access control enforces "cannot access ANYTHING except explicitly allowed folders" rules. AppArmor and SELinux configure these restrictions differently.

	AppArmor: Path-based. Specializes in restricting applications individually. Relatively easy to manage. High security, but restrictions break if filenames changes.

	SELinux: Label-based. Manages files by giving them types. More for technicians as they have complicated policies. Very high security with file tracking abilities.

### Firewall

Debian uses UFW (Uncomplicated Firewall). Firewalls restrict access from outside.

	UFW: Simple readable commands that equal complex iptables syntax. In other words, short cut commands that UFW translates to preset rules. Controls individual ports.

	Firewalld: Dynamic zone-based. Adjusts trust level by network zones. Smart firewall that understands network context. Perfect for enterprises.

	If UFW is like a door lock, firewalld is like a smart security system.

### Virtual Machine

A virtual machine (VM) is a software emulation of a complete computer system. A hypervisor creates and manages VMs by allocating host resources (CPU, memory, storage). There are three main virtualization types:
1. Bare-metal (Type 1 hypervisor): Runs directly on hardware. Highest security. No host OS attack surface. Compromise stays contained to that VM.

        I would use this for production servers.

2. Hosted (Type 2): Runs like a normal app inside your existing OS (Windows, Mac). Each VM is isolated from the others. A hacked guest VM rarely hurts the host but if someone hacks your main OS, all the VMs inside die too.

	    I would use this for testing multiple environments on one machine.

3. Containers: Not true VMs. They package just your app + its libraries/configs into a lightweight "bubble" that shares the host's kernel (core OS engine). No full guest OS needed, so they start in seconds and use 10x less resources than VMs. Think of it like object oriented programming for apps.
- Security Trade-off: Lower isolation. Kernel bugs let attacks escape to host/other containers (unlike VMs' full walls). Fine for dev/trusted code.
- Portability Superpower: Build once, run anywhere with Docker (Mac/Win use tiny Linux VM underneath for kernel compatability). No matter where you docker pull and run it (your laptop, US cloud server, friend's PC, or Tokyo data center), the app behaves identically with the same speed, features, and bugs (good and bad).

	    I would use this for:
		- Dev stuff: Copy the real live server setup in seconds so your team can test safely.
		- Microservices: Chop your big app into small pieces (like "login box," "buy button box"). Make more copies of just the busy ones.
		- Cloud: Google runs billions of containers daily on its cloud platform to power services like YouTube, where video recommendations, playback, and search features each run in lightweight, isolated containers orchestrated by Kubernetes.
		This setup lets Google scale specific parts, (like handling a viral video surge), without firing up full virtual machines for everything, making it faster and more efficient than traditional VMs.
			Why Containers Beat VMs Here:
			- Containers package just the app code and dependencies, sharing the host OS kernel for minimal overhead.
			- VMs emulate entire OSes, which is bulkier for microservices like YouTube's ad serving or live streaming.
			Everyday Impact:
			- You interact with these when watching videos; Kubernetes auto-scales containers to keep playback smooth during peaks.

### Hypervisor Choice

I chose VirtualBox because it is cross-platform and perfect for learning system admin. Zero risk while replicating real hardware simulation. I can use it like a test lab. Cross-platform means I can run multiple OSs and test in different environments.

	VirtualBox: High versatility. Cross-platform so no problems with different environments. All-purpose, jack-of-all-trades.

	UTM: Specialized optimization. Apple Silicon only but blazing fast. Simple Mac-native UI with low overhead. What it lacks in generality, it makes up for in simplicity and speed.
</details>

&nbsp;
---
&nbsp;

<details>
<summary>🇯🇵 日本語版　README</summary>

## Description

Born2BeRoot は、自分専用の仮想マシンを作成し、基本的なセキュリティ機能を備えたシンプルなサーバーを構築するプロジェクトです。
少なくとも 2 つの暗号化パーティションを LVM を使って作成しなければなりません。
OS として Debian か Rocky を選択できます。
ファイアウォール、SSH、強力なパスワードポリシー、sudo、そして 10 分ごとにすべてのターミナルに指定された情報を表示するスクリプトファイルを追加する必要があります。

## Instructions

VirtualBox を開き、katakaha の VM の「Start」を押します。
起動したら、パスワード「12345678aA」でディスクのロックを解除します。
ディスクのロック解除後は、ローカルホスト側のターミナルから「ssh」で VM のターミナルへアクセスできます。
次のコマンドを実行します:
`ssh katakaha@localhost -p 4242`
パスワードの入力を求められたら「1qwertyuiopZ」を入力します。
katakaha@localhost の部分を他のユーザー名に変えることで、別のユーザーとしてアクセスできます。
ユーザーの切り替えには `su` コマンドを使用します。

シグネチャは `shasum "katakaha_s VM.vdi"` で確認できます。
ファイルの場所は `/sgoinfre/b2br - vm/katakaha_s VM/` です。
`cat ~/[path]/signature.txt` の出力と比較してください。

以下に、レビューで必要な項目を確認するための便利なコマンドをまとめています。
<table>
    <thead>
        <tr>
            <th>カテゴリ</th>
            <th>コマンド</th>
            <th>内容 / 目的</th>
        </tr>
    </thead>
    <tbody>
		<!-- システムと認証 -->
		<tr>
    		<td>システム</td>
    		<td><code>uname -a</code></td>
    		<td>カーネル名とバージョン</td>
    		<td></td>
		</tr>
		<tr>
    		<td></td>
    		<td><code>hostnamectl</code></td>
    		<td>ホスト名とOS情報</td>
    		<td>✅</td>
		</tr>
		<tr>
    		<td></td>
    		<td><code>sudo hostnamectl set-hostname [新しい名前]</code> または <code>sudo visudo</code> で /etc/hostname を開く</td>
    		<td>ホスト名を変更（IPホスト名も忘れずに変更）</td>
    		<td>✅</td>
		</tr>
		<tr>
    		<td></td>
    		<td><code>sudo nano /etc/hosts</code> でIP名を新しい名前に変更</td>
    		<td>IPホスト名を変更</td>
    		<td>✅</td>
		</tr>
  		<!-- ユーザ＆グループ -->
    	<tr>
        	<td>ユーザ/グループ</td>
        	<td><code>sudo adduser [user]</code></td>
        	<td>ユーザー作成</td>
        	<td>✅</td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>sudo deluser [user]</code></td>
        	<td>ユーザー削除</td>
        	<td></td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>sudo addgroup [group]</code></td>
        	<td>グループ作成</td>
        	<td></td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>sudo delgroup [group]</code></td>
        	<td>グループ削除</td>
        	<td></td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>sudo usermod -aG [group] [user]</code></td>
        	<td>ユーザをグループに追加</td>
        	<td></td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>groups [user]</code></td>
        	<td>ユーザのグループを表示</td>
        	<td></td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>sudo passwd [user]</code></td>
        	<td>ユーザのパスワードを変更</td>
        	<td></td>
    	</tr>
    	<!-- パッケージ、サービス、ファイアウォール -->
    	<tr>
        	<td>パッケージ/サービス/ファイアウォール</td>
        	<td><code>dpkg -l | grep [pkg]</code></td>
        	<td>パッケージがインストールされているか確認</td>
        	<td></td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>systemctl status [service]</code></td>
        	<td>サービス状態を確認</td>
        	<td>✅</td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>sudo systemctl is-enabled [service]</code></td>
        	<td>起動時に有効か確認</td>
        	<td></td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>sudo systemctl [start,stop,restart] [service]</code></td>
        	<td>サービス管理</td>
        	<td></td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>sudo ufw status verbose</code></td>
        	<td>ファイアウォールルール表示</td>
        	<td>✅</td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>sudo ufw allow [port]</code></td>
        	<td>ポート[番号]を許可</td>
        	<td></td>
    	</tr>
    	<!-- SSH＆ネットワーク -->
    	<tr>
        	<td>SSH/ネットワーク</td>
        	<td><code>ss -tnlp | grep ssh</code> または <code>ss -tuln</code></td>
        	<td>待ち受けポート確認</td>
        	<td></td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>sudo systemctl status ssh</code></td>
        	<td>SSH確認</td>
        	<td></td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>ip a</code></td>
        	<td>IPアドレス表示</td>
        	<td></td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>hostname -I</code></td>
        	<td>IPアドレス（短縮版）</td>
        	<td></td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>ssh [username]@[IP] -p [port番号]</code></td>
        	<td>SSH接続</td>
        	<td></td>
    	</tr>
    	<!-- ディスク、LVM、パーティション -->
    	<tr>
        	<td>LVM/ディスク/パーティション</td>
        	<td><code>lsblk</code></td>
        	<td>ブロックデバイスとマウントポイント表示</td>
        	<td>✅</td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>df -h</code></td>
        	<td>ファイルシステムごとのディスク使用量</td>
        	<td></td>
    	</tr>
    	<!-- ログ＆sudo設定 -->
    	<tr>
        	<td>Sudo/ログ</td>
        	<td><code>sudo visudo</code></td>
        	<td>sudoersを安全に編集</td>
        	<td></td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>sudo cat /etc/sudoers</code></td>
        	<td>sudoers表示</td>
        	<td></td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>sudo cat /etc/sudoers.d/[file]</code></td>
        	<td>カスタムsudo設定表示</td>
        	<td></td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>journalctl -xe</code></td>
        	<td>最近のシステムログ</td>
        	<td></td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>sudo tail -n 50 /var/log/auth.log</code></td>
        	<td>認証/sudoログ</td>
        	<td></td>
    	</tr>
    	<!-- Cron＆監視スクリプト -->
    	<tr>
        	<td>Cron/monitoring.sh</td>
        	<td><code>crontab -l</code></td>
        	<td>現在のユーザcrontab表示</td>
        	<td></td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>sudo crontab -l</code></td>
        	<td>root crontab表示</td>
        	<td></td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>systemctl list-timers</code></td>
        	<td>タイマ一覧</td>
        	<td></td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>bash monitoring.sh</code></td>
        	<td>スクリプトを手動実行</td>
        	<td></td>
    	</tr>
    	<!-- ポリシー -->
    	<tr>
        	<td>ポリシー</td>
        	<td><code>sudo nano /etc/pam.d/common-password</code></td>
        	<td>パスワード設定用のパスワードポリシー確認</td>
        	<td>✅</td>
    	</tr>
    	<tr>
        	<td></td>
        	<td><code>chage -l [user]</code></td>
        	<td>ユーザのパスワードポリシー表示</td>
        	<td>✅</td>
    	</tr>
	</tbody>
</table>

## Resources

このプロジェクトの進め方の全体像は、次のサイトを参考にしました。
セットアップ手順の最初のステップを理解するのに役立ちました。
[Baigalmaa Baatar](https://baigal.medium.com/born2beroot-e6e26dfb50ac)<br>

レビュー対策には、次のサイトを参考にしました。
各項目について、防御的な観点から解説されています。
[jizo](https://note.com/jizo_ts/nResources12a7b)

#### 他に参考にしたリソース

- [Sudoers Manual](https://www.sudo.ws/docs/man/1.9.13/sudoers.man/)

- [OpenSSH Manual](https://www.openssh.org/manual.html)

- [Debian Documentation](https://www.debian.org/doc/manuals/debian-reference/index.en.html)

#### AI を使って理解を深めたこと

- このプロジェクトが教えてくれること

- 各要素が何をしているのか

- 情報をどこで調べればよいか

## Project Description

このプロジェクトでは、ハイパーバイザーを使用して仮想マシンを一から構築し、
CLI のみで設定を行います。

設定した内容:
- セキュリティポリシー（SSH、AppArmor、UFW）
- ユーザー管理（sudo、厳格なパスワードポリシー）
- パーティショニング（LVM を使用した root と swap）
- インストールしたサービス（sudo、openssh-server、ufw、libpam-pwquality）
- 監視（cron による定期的なシステム状態レポート）

### OS

本プロジェクトでは Debian と Rocky Linux のどちらかを選択できます。
両者はどちらもサーバー用途に適した Linux ディストリビューションですが、
設計思想と想定ユースケースが異なります。


    Rocky Linux:
    エンタープライズ環境を想定したディストリビューションで、
    RHEL（Red Hat Enterprise Linux）と互換性のある設計を採用しています。
    長期サポートと一貫したセキュリティポリシーを提供し、
    ミッションクリティカルなサーバー環境に適しています。
    CentOS の後継として位置づけられているため、
    既存の RHEL / CentOS 環境からの移行も比較的容易です。

    Rocky Linux のデメリット:
    安定性を最優先する設計のため、ソフトウェア更新が遅く、
    パッケージのバージョンが古くなりがちです。
    Debian と比べるとコミュニティ規模が小さく、
    情報やドキュメントの量が限られています。
    デスクトップ用途にはあまり向いていません。


    Debian:
    DFSG（Debian Free Software Guidelines）に準拠したソフトウェアを重視する
    コミュニティ主導のオープンソース OS です。
    安定性とセキュリティを重視した開発方針を持ち、
    新機能を急いで導入するのではなく、
    実績のある安定したソフトウェアにセキュリティパッチを適用することで
    攻撃対象領域を最小限に抑えています。
    多くの Linux ディストリビューションのベースになっているため、
    トラブルシューティングに関する情報が非常に豊富です。

    Debian のデメリット:
    stable ブランチではソフトウェアのバージョンが古くなる傾向があり、
    最新機能や新しいハードウェア対応が必要な場合には制約があります。
    初心者にとっては初期設定が複雑に感じられる場合があります。


本プロジェクトでは、これらの特性を理解した上で Debian を選択しました。


### Firewall

Debian では UFW（Uncomplicated Firewall）を使用します。
UFW は iptables を簡潔なコマンドで操作できる仕組みです。

UFW がドアの鍵だとすると、
firewalld はスマートセキュリティシステムのような存在です。


### Virtual Machine

仮想マシン（VM）は、完全なコンピュータをソフトウェアで再現したものです。
ハイパーバイザーが CPU、メモリ、ストレージを割り当てて管理します。

仮想化には主に次の 3 種類があります。

1. ベアメタル（Type 1）
   ハードウェア上で直接動作。最高の分離性とセキュリティ。

2. ホスト型（Type 2）
   通常の OS 上でアプリとして動作。学習や検証向け。

3. コンテナ
   カーネルを共有する軽量な仮想化。高速だが分離性は低い。

#### ハイパーバイザー選定理由

クロスプラットフォームで利用でき、システム管理の学習に最適だと考え、
VirtualBox を選択しました。
実際のハードウェア構成を再現しつつもリスクはなく、
テスト用のラボ環境として扱うことができます。
また、クロスプラットフォームであるため、
複数の OS を実行して異なる環境を検証できる点も利点です。

	VirtualBox:
	汎用性が高く、クロスプラットフォーム対応のため
	異なる環境でも問題なく使用できます。
	オールラウンドに使える、いわば万能型のハイパーバイザーです。

	UTM:
	Apple Silicon に特化した最適化が施されており、
	非常に高速に動作します。
	Mac ネイティブのシンプルな UI と低オーバーヘッドが特徴です。
	汎用性は低いものの、その分シンプルさと速度に優れています。
</details>

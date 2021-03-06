
## CentOS Repo

CentOS 預設的套件庫並不及 Debian 來的完整 (豐富) ，但很棒的是有第三方來源的套件庫可以使用。著名的有 RPMforge, EPEL ... 等，建議先行安裝 RPMforge 後再使用其它來源會簡單些。 

### RPMforge

下載 RPMForge 安裝檔。

	# 64 bit
	wget http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el6.rf.x86_64.rpm
	
	# 32 bit
	wget http://pkgs.repoforge.org/rpmforge-release/rpmforge-release-0.5.3-1.el6.rf.i686.rpm

匯入 DAG 的 RPM GPG 金鑰。

	rpm --import http://apt.sw.be/RPM-GPG-KEY.dag.txt

若看到以下訊息則表示先前已匯過。

	error: http://apt.sw.be/RPM-GPG-KEY.dag.txt: key 1 import failed.

驗證套件，查看此安裝是否為 DAG 所簽證，就算是在 Linux 上也是得避免安裝來路不名的軟體。

	rpm -K rpmforge-release-0.5.2-2.el6.rf.*.rpm

<!> 安全性警告： rpmforge-release 這個套件會將數條 GPG 金鑰匯入你的 RPM 資料庫內。你若已審核過確套件的 md5sum，並信任 Dag 等人，那麼它的安全性便延伸自你對他們的信任。

安裝。

	rpm -i rpmforge-release-0.5.2-2.el6.rf.*.rpm

這樣做會新增一個 yum 軟件庫的設定檔及匯入應有的 GPG 金鑰。

現在可以使用 yum 來安裝 RPMForge 來源的套件了。

	yum install htop

### EPEL

下載 EPEL 安裝檔。

	$ wget http://mirror-fpt-telecom.fpt.net/fedora/epel/6/i386/epel-release-6-8.noarch.rpm

Install **epel**.

	$ sudo rpm -ivh epel-release-6-8.noarch.rpm

Search package.

	$ yum search drush
	Loaded plugins: fastestmirror, refresh-packagekit, security
	Loading mirror speeds from cached hostfile
	 * base: ftp.nsysu.edu.tw
	 * epel: mirror01.idc.hinet.net
	 * extras: ftp.nsysu.edu.tw
	 * rpmforge: mirrors.neusoft.edu.cn
	 * updates: ftp.nsysu.edu.tw
	==================================== N/S Matched: drush ====================================
	drupal6-drush.noarch : Drush command line shell for Drupal6
	drupal7-drush_language.noarch : Drush language commands
	php-channel-drush.noarch : Adds pear.drush.org channel to PEAR
	php-drush-drush.noarch : Command line shell and Unix scripting interface for Drupal
	
	  Name and summary matches only, use "search all" for everything.

watch Info

	$ yum info php-drush-drush.noarch
	Loaded plugins: fastestmirror, refresh-packagekit, security
	Determining fastest mirrors
	 * base: ftp.nsysu.edu.tw
	 * epel: mirror01.idc.hinet.net
	 * extras: ftp.nsysu.edu.tw
	 * rpmforge: mirrors.neusoft.edu.cn
	 * updates: ftp.nsysu.edu.tw
	Installed Packages
	Name        : php-drush-drush
	Arch        : noarch
	Version     : 5.9.0
	Release     : 1.el6
	Size        : 1.5 M
	Repo        : installed
	From repo   : epel
	Summary     : Command line shell and Unix scripting interface for Drupal
	URL         : http://www.drush.org
	License     : GPLv2+
	Description : Drush is a command line shell and Unix scripting interface for Drupal.  If
	            : you are unfamiliar with shell scripting, reviewing the documentation for your
	            : shell (e.g. man bash) or reading an online tutorial (e.g. search for "bash
	            : tutorial") will help you get the most out of Drush.
	            : 
	            : Drush core ships with lots of useful commands for interacting with code like
	            : modules/themes/profiles. Similarly, it runs update.php, executes sql queries
	            : and DB migrations, and misc utilities like run cron or clear cache.
	            : 
	            : Works with Drupal 6, Drupal 7, and usually Drupal 8.

install package with yum of epel source.

現在可以使用 yum 來安裝 RPMForge 來源的套件了。
	$ sudo yum install php-drush-drush

### Reference

[RPMForge - CentOS Wiki](http://wiki.centos.org/zh-tw/AdditionalResources/Repositories/RPMForge)
[Install and Enable RPMForge Repository in RHEL/CentOS 6, 5, 4](http://www.tecmint.com/install-and-enable-rpmforge-repository-in-rhel-centos-6-5-4/)
[CentOS / RHEL / Scientific Linux 6 Enable & Install EPEL Repo](http://www.cyberciti.biz/faq/fedora-sl-centos-redhat6-enable-epel-repo/)
[EPEL - FedoraProject](http://fedoraproject.org/wiki/EPEL)

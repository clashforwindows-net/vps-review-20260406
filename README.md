# VPS 鑷缓閭欢鏈嶅姟鍣ㄤ笌閫氫俊鏈嶅姟瀹屽叏瀹炴垬

**鍒嗙被**锛歏PS 閫氫俊鍩虹璁炬柦 | **鏇存柊鏃ユ湡**锛?026-09-24 | **缁存姢浜?*锛歝lashforwindows-net

---

## 馃摉 鐩綍

- [涓€銆侀偖浠舵湇鍔″櫒鏋舵瀯娣卞害瑙ｆ瀽](#涓€閭欢鏈嶅姟鍣ㄦ灦鏋勬繁搴﹁В鏋?
- [浜屻€丳ostfix + Dovecot 閭欢绯荤粺閮ㄧ讲](#浜宲ostfix--dovecot-閭欢绯荤粺閮ㄧ讲)
- [涓夈€丼PF / DKIM / DMARC 閭欢璁よ瘉閰嶇疆](#涓塻pf--dkim--dmarc-閭欢璁よ瘉閰嶇疆)
- [鍥涖€侀偖浠跺畨鍏ㄤ笌鍙嶅瀮鍦鹃偖浠禲(#鍥涢偖浠跺畨鍏ㄤ笌鍙嶅瀮鍦鹃偖浠?
- [浜斻€乄ebmail 閭欢瀹㈡埛绔厤缃甝(#浜攚ebmail-閭欢瀹㈡埛绔厤缃?
- [鍏€侀偖浠跺垪琛ㄦ湇鍔★紙Mailman3锛塢(#鍏偖浠跺垪琛ㄦ湇鍔ailman3)
- [涓冦€佽嚜鎵樼鍗忎綔閫氫俊濂椾欢](#涓冭嚜鎵樼鍗忎綔閫氫俊濂椾欢)
- [鍏€侀偖浠剁洃鎺т笌鏃ュ織鍒嗘瀽](#鍏偖浠剁洃鎺т笌鏃ュ織鍒嗘瀽)
- [涔濄€侀偖浠剁郴缁熻繍缁磋剼鏈笌宸ュ叿绠盷(#涔濋偖浠剁郴缁熻繍缁磋剼鏈笌宸ュ叿绠?
- [鍗併€佸父瑙侀棶棰樹笌鏁呴殰鎺掓煡](#鍗佸父瑙侀棶棰樹笌鏁呴殰鎺掓煡)

---

## 涓€銆侀偖浠舵湇鍔″櫒鏋舵瀯娣卞害瑙ｆ瀽

### 1.1 閭欢鍙戦€侀摼璺畬鏁磋В鏋?
褰撶敤鎴峰彂閫佷竴灏侀偖浠舵椂锛屾暟鎹寘缁忓巻浠ヤ笅瀹屾暣璺緞锛?
```
鍙戜欢浜猴紙MUA/MUA瀹㈡埛绔級
    鈹?    鈻?SMTP 鍗忚锛堢鍙?587 鎻愪氦锛?MTA 鍙戦€佹湇鍔″櫒锛圥ostfix / Exim锛?    鈹?    鈹溾攢鈹€ DNS 鏌ヨ MX 璁板綍
    鈹?    鈻?SMTP 鍗忚锛堢鍙?25 浼犺緭锛?鏀朵欢鏂?MTA锛堝鏂归偖浠舵湇鍔″櫒锛?    鈹?    鈻?MDA 鎶曢€掍唬鐞嗭紙Dovecot LDA / LMTP锛?    鈹?    鈻?鏀朵欢浜洪偖绠憋紙Maildir / mbox 瀛樺偍锛?```

**鍏抽敭绔彛瀵圭収琛?*锛?
| 绔彛 | 鍗忚 | 鐢ㄩ€?| 瀹夊叏 |
|------|------|------|------|
| 25 | SMTP | MTA 涔嬮棿閭欢浼犺緭 | 鏄庢枃锛?STARTTLS锛墊
| 465 | SMTPS | SMTP 鎻愪氦锛堝巻鍙查仐鐣欙級 | SSL/TLS |
| 587 | Submission | MUA 鎻愪氦閭欢 | STARTTLS 鍔犲瘑 |
| 993 | IMAPS | 閭欢璇诲彇锛堝姞瀵嗭級 | TLS |
| 995 | POP3S | POP3 閭欢璇诲彇 | TLS |
| 110 | POP3 | 閭欢璇诲彇锛堟槑鏂囷級 | 鉂?|
| 143 | IMAP | 閭欢璇诲彇锛堟槑鏂囷級 | 鉂?|

### 1.2 鑷缓閭欢鏈嶅姟鍣ㄧ殑鏍稿績浠峰€?
| 瀵规瘮椤?| 鑷缓閭欢鏈嶅姟鍣?| Gmail / 浼佷笟閭 |
|--------|--------------|----------------|
| 鏁版嵁涓绘潈 | 瀹屽叏鎺屾帶锛屾暟鎹笉鍑哄 | 鏁版嵁瀛樺偍鍦ㄧ涓夋柟 |
| 鎴愭湰 | VPS 鎴愭湰锛?5-30/鏈堬級 | $6-12/鐢ㄦ埛/鏈?|
| 鍙戦€侀檺鍒?| 鍙栧喅浜?VPS 甯﹀鍜?IP 淇¤獕 | 鏈変弗鏍肩殑鍙戦€侀厤棰?|
| 鐏垫椿鎬?| 鏃犻檺鍒悕/鍩熷悕/鐢ㄦ埛 | 鍙楀埗浜庡椁愰檺鍒?|
| 闅愮 | 鏈€楂橈紙绔埌绔姞瀵嗗彲閫夛級 | 鍙楀埗浜庢湇鍔″晢 |
| 缁存姢闅惧害 | 楂橈紙闇€鎸佺画缁存姢 IP 淇¤獕锛?| 闆剁淮鎶?|

### 1.3 閭欢绯荤粺缁勪欢閫夊瀷

| 缁勪欢 | 鎺ㄨ崘鏂规 | 澶囬€?| 璇存槑 |
|------|---------|------|------|
| **MTA** | **Postfix** | Exim, OpenSMTPD | Postfix 閰嶇疆绠€娲併€佸畨鍏ㄦ€ч珮 |
| **IMAP/POP** | **Dovecot** | Courier | 鍔熻兘瀹屾暣锛孖MAP 鎬ц兘浼樼 |
| **Webmail** | **Roundcube** | SquirrelMail, RainLoop | UI 鐜颁唬鍖栵紝鎻掍欢涓板瘜 |
| **閭欢鍒楄〃** | **Mailman3** | Sympa | Python 缂栧啓锛岀ぞ鍖烘椿璺?|
| **鍙嶇梾姣?* | **ClamAV** | - | 寮€婧愶紝闆嗘垚鑹ソ |
| **鍙嶅瀮鍦?* | **Rspamd** | SpamAssassin | 閫熷害蹇紝鍑嗙‘鐜囬珮 |
| **閭欢褰掓。** | **MailArchiva** | - | 鍚堣鎬у瓨鍌?|
| **鐢ㄦ埛璁よ瘉** | **Dovecot SASL** | 绯荤粺鐢ㄦ埛 | 瀹夊叏鍙潬 |

---

## 浜屻€丳ostfix + Dovecot 閭欢绯荤粺閮ㄧ讲

### 2.1 绯荤粺鐜鍑嗗

```bash
#!/bin/bash
# prepare-mail-server.sh - 閭欢鏈嶅姟鍣ㄥ墠鏈熷噯澶?set -e

echo "=== 閭欢鏈嶅姟鍣ㄧ幆澧冨噯澶?==="

# 1. 瀹夎鍩虹杞欢
apt-get update && apt-get install -y \
    postfix postfix-mysql postfix-pcre \
    dovecot-core dovecot-imapd dovecot-lmtpd dovecot-mysql \
    dovecot-solr \
    clamav clamav-daemon \
    rspamd \
    mariadb-server \
    roundcube roundcube-core roundcube-mysql \
    certbot \
    fail2ban \
    analytics-awk

# 2. 閰嶇疆涓绘満鍚嶏紙蹇呴』锛侀偖浠舵湇鍔″櫒FQDN锛?HOSTNAME="mail"
DOMAIN="example.com"
FULL_HOSTNAME="${HOSTNAME}.${DOMAIN}"

hostnamectl set-hostname "$FULL_HOSTNAME"
echo "$FULL_HOSTNAME" > /etc/hostname

# 3. 閰嶇疆 /etc/hosts锛堜繚璇佹湰鍦拌В鏋愭纭級
cat >> /etc/hosts << EOF
127.0.0.1 $FULL_HOSTNAME $HOSTNAME
EOF

# 4. 寮€鏀鹃槻鐏绔彛
ufw allow 25/tcp    # SMTP
ufw allow 465/tcp    # SMTPS
ufw allow 587/tcp    # Submission
ufw allow 993/tcp    # IMAPS
ufw allow 995/tcp    # POP3S
ufw allow 443/tcp    # Roundcube Webmail
ufw allow 80/tcp     # Let's Encrypt

echo "[OK] 鐜鍑嗗瀹屾垚"
echo "涓绘満鍚? $FULL_HOSTNAME"
```

### 2.2 Postfix 涓婚厤缃枃浠?
```bash
# /etc/postfix/main.cf - Postfix 涓婚厤缃紙瀹屾暣鐗堬級

# ===== 鍩烘湰閰嶇疆 =====
myhostname = mail.example.com
mydomain = example.com
myorigin = $mydomain
mydestination = $myhostname, localhost, localhost.$mydomain, $mydomain
mynetworks = 127.0.0.0/8 10.0.0.0/24
inet_interfaces = all
inet_protocols = ipv4

# ===== 閭欢澶у皬闄愬埗 =====
mailbox_size_limit = 524288000        # 500 MB
message_size_limit = 52428800         # 50 MB
virtual_mailbox_limit = 52428800

# ===== 铏氭嫙鍩熼厤缃?=====
virtual_alias_maps = mysql:/etc/postfix/mysql/virtual_alias_maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql/virtual_mailbox_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql/virtual_mailbox_maps.cf
virtual_transport = lmtp:unix:private/dovecot-lmtp

# ===== 瀹夊叏閰嶇疆 =====
smtpd_tls_cert_file = /etc/letsencrypt/live/mail.example.com/fullchain.pem
smtpd_tls_key_file = /etc/letsencrypt/live/mail.example.com/privkey.pem
smtpd_tls_security_level = may
smtpd_tls_protocols = !SSLv2, !SSLv3, !TLSv1, !TLSv1.1
smtpd_tls_ciphers = high
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom

# ===== SMTP 瀹㈡埛绔厤缃紙鍙戦€侀偖浠讹級 =====
smtp_tls_security_level = may
smtp_tls_protocols = !SSLv2, !SSLv3, !TLSv1, !TLSv1.1
smtp_tls_ciphers = high
smtp_tls_wrappermode = no

# ===== SASL 璁よ瘉 =====
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous, noplaintext
smtpd_sasl_tls_security_options = noanonymous

# ===== Helo 闄愬埗 =====
smtp_helo_required = yes
strict_rfc821_envelopes = yes
disable_vrfy_command = yes

# ===== 閫熺巼闄愬埗锛堥槻姝㈡互鐢級 =====
smtpd_client_connection_count_limit = 10
smtpd_client_connection_rate_limit = 30
smtp_destination_rate_delay = 1s

# ===== 鍐呭杩囨护锛堥€氳繃 Rspamd锛?=====
content_filter = smtp:[127.0.0.1]:10024
receive_override_options = no_address_mapped

# ===== 鏃ュ織鏍煎紡 =====
maillog_file = /var/log/postfix.log
maillog_compress = yes
maillog_flush = yes
```

### 2.3 MySQL 鏁版嵁搴撻厤缃?
```sql
-- 鍒涘缓閭欢鏁版嵁搴撳拰鐢ㄦ埛
CREATE DATABASE mailserver CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'mailuser'@'localhost' IDENTIFIED BY 'MAIL_PASSWORD_STRONG';
GRANT SELECT ON mailserver.* TO 'mailuser'@'localhost';

USE mailserver;

-- 铏氭嫙鍩熷悕琛?CREATE TABLE virtual_domains (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL UNIQUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- 铏氭嫙鐢ㄦ埛琛?CREATE TABLE virtual_users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    domain_id INT NOT NULL,
    email VARCHAR(255) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (domain_id) REFERENCES virtual_domains(id) ON DELETE CASCADE,
    INDEX idx_email (email)
);

-- 铏氭嫙鍒悕琛紙閭欢杞彂锛?CREATE TABLE virtual_aliases (
    id INT AUTO_INCREMENT PRIMARY KEY,
    domain_id INT NOT NULL,
    source VARCHAR(255) NOT NULL,
    destination VARCHAR(255) NOT NULL,
    FOREIGN KEY (domain_id) REFERENCES virtual_domains(id) ON DELETE CASCADE,
    INDEX idx_source (source)
);

-- 鎻掑叆绀轰緥鏁版嵁
INSERT INTO virtual_domains (name) VALUES ('example.com');
INSERT INTO virtual_domains (name) VALUES ('mail.example.com');

-- 鐢熸垚鍔犲瘑瀵嗙爜锛圖ovecot 绠＄悊宸ュ叿锛?-- doveadm pw -s SHA512-CRYPT -p 'YourPassword123'
INSERT INTO virtual_users (domain_id, email, password) VALUES
    (1, 'user1@example.com', '{SHA512-CRYPT}$6$xxxxxxx'),
    (1, 'admin@example.com', '{SHA512-CRYPT}$6$yyyyyyy'),
    (1, 'contact@example.com', '{SHA512-CRYPT}$6$zzzzzzz');

-- 閭欢杞彂瑙勫垯
INSERT INTO virtual_aliases (domain_id, source, destination) VALUES
    (1, 'postmaster@example.com', 'admin@example.com'),
    (1, 'support@example.com', 'admin@example.com'),
    (1, 'sales@example.com', 'user1@example.com,admin@example.com');
```

### 2.4 Dovecot 閰嶇疆

```bash
# /etc/dovecot/dovecot.conf
protocols = imap pop3 lmtp sieve
listen = *, ::

# 绂佺敤涓嶅畨鍏ㄧ殑鍗忚
disable_plaintext_auth = yes

# 璁よ瘉
!include auth-sql.conf.ext

# SSL/TLS
ssl = required
ssl_cert = </etc/letsencrypt/live/mail.example.com/fullchain.pem
ssl_key = </etc/letsencrypt/live/mail.example.com/privkey.pem
ssl_min_protocol = TLSv1.2
ssl_cipher_list = ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384
ssl_prefer_server_ciphers = yes
ssl_dh = </usr/share/dovecot/dh.pem

# 閭欢瀛樺偍
mail_location = maildir:/var/mail/vhosts/%d/%n
mail_uid = 5000
mail_gid = 5000
mail_plugins = "quota"

# LMTP锛堟湰鍦版姇閫掞紝涓?Postfix 闆嗘垚锛?service lmtp {
    unix_listener /var/spool/postfix/private/dovecot-lmtp {
        mode = 0600
        user = postfix
        group = postfix
    }
}

# 璁よ瘉锛堜笌 Postfix 闆嗘垚锛?service auth {
    unix_listener /var/spool/postfix/private/auth {
        mode = 0660
        user = postfix
        group = postfix
    }
    unix_listener auth-userdb {
        mode = 0600
        user = vmail
        group = vmail
    }
}

# 鏃ュ織
log_path = /var/log/dovecot.log
info_log_path = /var/log/dovecot-info.log
debug_log_path = /var/log/dovecot-debug.log
```

---

## 涓夈€丼PF / DKIM / DMARC 閭欢璁よ瘉閰嶇疆

### 3.1 涓轰粈涔堥渶瑕侀偖浠惰璇?
閭欢璁よ瘉鏄槻姝㈠煙鍚嶈鐢ㄤ簬浼€犲彂浠朵汉鍦板潃锛堥挀楸奸偖浠讹級鐨勫叧閿妧鏈€傛湭閰嶇疆鐨勫煙鍚嶅彂閫佺殑閭欢鏈夋瀬楂樻鐜囪 Gmail銆丱utlook 绛変富娴侀偖绠辨湇鍔″晢鎷掓敹鎴栨爣璁颁负鍨冨溇閭欢銆?
### 3.2 SPF 閰嶇疆锛堝彂浠舵湇鍔″櫒鎺堟潈锛?
**DNS TXT 璁板綍**锛?```dns
example.com.  IN  TXT  "v=spf1 mx a ip4:YOUR_VPS_IP include:_spf.mail.example.com ~all"
```

| SPF 鏈哄埗 | 鍚箟 |
|---------|------|
| `v=spf1` | SPF 鐗堟湰鍙?|
| `mx` | 鍏佽 MX 璁板綍涓殑鎵€鏈夋湇鍔″櫒鍙戦€侀偖浠?|
| `a` | 鍏佽 A 璁板綍涓殑 IP |
| `ip4:X.X.X.X` | 鍏佽鎸囧畾 IP |
| `include:_spf.google.com` | 鍏佽 Google 鏈嶅姟鍣紙浣跨敤 Google Workspace 鏃讹級|
| `~all` | 杞け璐ワ紙寤鸿鐢ㄤ簬娴嬭瘯锛? `~all` / `-all`锛堢‖澶辫触锛岀敓浜х幆澧冿級|

### 3.3 DKIM 閰嶇疆锛堥偖浠剁鍚嶏級

```bash
# 1. 瀹夎 OpenDKIM
apt-get install -y opendkim opendkim-tools

# 2. 鐢熸垚 DKIM 瀵嗛挜瀵?mkdir -p /etc/opendkim/keys/example.com
opendkim-genkey -D /etc/opendkim/keys/example.com/ \
    -d example.com -s mail -v

mv /etc/opendkim/keys/example.com/mail.private \
    /etc/opendkim/keys/example.com/default
mv /etc/opendkim/keys/example.com/mail.txt \
    /etc/opendkim/keys/example.com/default.txt

chown -R opendkim:opendkim /etc/opendkim/keys
chmod 600 /etc/opendkim/keys/example.com/default

# 3. 鏌ョ湅鍏挜锛堟坊鍔犲埌 DNS锛?cat /etc/opendkim/keys/example.com/default.txt
# 杈撳嚭绫讳技锛?# mail._domainkey IN TXT ( "v=DKIM1; k=rsa; p=MIGfMA0GCSq..." )
```

**DNS TXT 璁板綍**锛堜粠 default.txt 澶嶅埗锛岀Щ闄ゅ紩鍙凤級锛?```dns
mail._domainkey.example.com.  IN  TXT  "v=DKIM1; k=rsa; p=MIGfMA0GCSqGSIb3DQEBAQUAA..."
```

**閰嶇疆 OpenDKIM 涓?Postfix 闆嗘垚**锛?
```bash
# /etc/opendkim.conf
Syslog                  yes
UMask                   002
KeyTable                /etc/opendkim/key.table
SigningTable            refile:/etc/opendkim/signing.table
ExternalIgnoreList      refile:/etc/opendkim/trusted.hosts
InternalHosts           refile:/etc/opendkim/trusted.hosts
OversignHeaders         From
Canonicalization         relaxed/simple
```

```bash
# /etc/opendkim/key.table
mail._domainkey.example.com example.com:mail:/etc/opendkim/keys/example.com/default

# /etc/opendkim/signing.table
*@example.com mail._domainkey.example.com

# /etc/opendkim/trusted.hosts
127.0.0.1
localhost
*.example.com
```

### 3.4 DMARC 閰嶇疆锛堢瓥鐣ユ姤鍛婏級

```dns
_dmarc.example.com.  IN  TXT  "v=DMARC1; p=quarantine; rua=mailto:dmarc-reports@example.com; ruf=mailto:dmarc-forensics@example.com; pct=100; adkim=r; aspf=r"
```

| DMARC 鍙傛暟 | 璇存槑 |
|-----------|------|
| `v=DMARC1` | 鐗堟湰 |
| `p=quarantine` | 绛栫暐锛歚none`(浠呯洃鎺? / `quarantine`(鍙枒閭欢闅旂) / `reject`(鎷掓敹) |
| `rua=mailto:...` | 鑱氬悎鎶ュ憡鍙戦€佸湴鍧€锛堟瘡鏃ュ彂閫侊級 |
| `ruf=mailto:...` | 澶辫触鎶ュ憡鍙戦€佸湴鍧€锛堝疄鏃跺彂閫侊級 |
| `pct=100` | 搴旂敤绛栫暐鐨勯偖浠剁櫨鍒嗘瘮 |
| `adkim=r` | DKIM 瀵归綈妯″紡锛坄r`瀹芥澗 / `s`涓ユ牸锛?|
| `aspf=r` | SPF 瀵归綈妯″紡锛坄r`瀹芥澗 / `s`涓ユ牸锛?|

### 3.5 Rspamd 闆嗘垚锛堟櫤鑳藉弽鍨冨溇锛?
```bash
# 瀹夎 Rspamd
apt-get install -y rspamd

# 閰嶇疆 Rspamd 涓?Postfix 闆嗘垚
# Postfix milter 閰嶇疆
cat >> /etc/postfix/main.cf << 'EOF'
# Rspamd milter
milter_protocol = 6
milter_default_action = accept
smtpd_milters = inet:127.0.0.1:11332
non_smtpd_milters = inet:127.0.0.1:11332
EOF

# Rspamd DKIM 绛惧悕閰嶇疆
cat > /etc/rspamd/local.d/dkim_signing.conf << 'EOF'
path = "/var/lib/rspamd/dkim/$domain.$selector.key";
selector_map = "/etc/rspamd/dkim_selectors.map";
key_table = "/etc/rspamd/dkim_keys.map";
allow_hdrfrom_mismatched_domains = false;
allow_pubkey_mismatched_domains = false;
use_domain = "header";
use_domain_from_message = true;
sign_authenticated = true;
sign_local = true;
use_esld = true;
check_pubkey = true;
EOF

# 鐢熸垚 DKIM 瀵嗛挜渚?Rspamd 浣跨敤
mkdir -p /var/lib/rspamd/dkim
cp /etc/opendkim/keys/example.com/default /var/lib/rspamd/dkim/example.com.default
chown _rspamd:_rspamd /var/lib/rspamd/dkim/example.com.default
chmod 640 /var/lib/rspamd/dkim/example.com.default

systemctl restart postfix rspamd
```

---

## 鍥涖€侀偖浠跺畨鍏ㄤ笌鍙嶅瀮鍦鹃偖浠?
### 4.1 Rspamd 鏅鸿兘杩囨护瑙勫垯

```bash
# /etc/rspamd/local.d/settings.conf
# 鑷畾涔夎繃婊よ鍒?
# 楂樹俊瑾夌櫧鍚嶅崟
whitelist {
    rcpt = "user@example.com";
    from = "/.*@trusted-sender\\.com$/";
    ip = ["10.0.0.0/8", "192.168.0.0/16"];
    priority = 10;  # 楂樹紭鍏堢骇
}

# 宸茬煡鍨冨溇閭欢榛戝悕鍗?blacklist {
    from = "/.*@(spam-domain|ads-mailer)\\..*$/";
    priority = 10;
}

# 鎴愪汉鍐呭杩囨护
adult_content {
    from = /.*@(adult-site|porn-mailer)\\..*$/;
    add_header = 1;
    score = 5.0;
}

# 閲戣瀺璇堥獥杩囨护
phishing_protection {
    # 妫€娴嬮挀楸奸摼鎺?    words = ["verify-your-account", "suspended-account", "urgent-action-required"];
    score = 3.0;
}
```

### 4.2 Postfix 璁块棶鎺у埗

```bash
# /etc/postfix/access - 璁块棶鎺у埗琛?# 缂栬緫鍚庤繍琛? postmap /etc/postfix/access

# 鍏佽鏈綉缁滃彂閫侊紙鏃犻渶璁よ瘉锛?10.0.0.0/8    OK

# 闄愬埗鐗瑰畾 IP 鍙戦€侀鐜?45.33.32.156  REJECT "Go away spammer"

# 鍏佽鐗瑰畾鍩熷悕鍙戝線鐗瑰畾鏀朵欢浜?@example.com  OK
marketing@example.com  RELAY

# 鐢熸垚 hash 琛?postmap /etc/postfix/access
```

### 4.3 Fail2ban 閭欢闃叉姢

```ini
# /etc/fail2ban/jail.local
[postfix]
enabled = true
port = smtp,465,submission
filter = postfix
logpath = /var/log/postfix.log
bantime = 3600
findtime = 600
maxretry = 5
action = iptables-allports

[dovecot]
enabled = true
port = pop3,pop3s,imap,imaps,submission,ssmtp
filter = dovecot
logpath = /var/log/dovecot.log
bantime = 3600
findtime = 600
maxretry = 10
action = iptables-allports

[rspamd]
enabled = true
port = 11332
filter = rspamd
logpath = /var/log/rspamd/rspamd.log
bantime = 600
findtime = 300
maxretry = 3
action = iptables-allports
```

---

## 浜斻€乄ebmail 閭欢瀹㈡埛绔厤缃?
### 5.1 Roundcube 瀹屾暣閰嶇疆

```bash
# /etc/roundcube/config.inc.php
<?php
$config = [];

// 鏁版嵁搴撻厤缃?$config['db_dsnw'] = 'mysql://roundcube:RC_PASSWORD@localhost/roundcube';

// IMAP 閰嶇疆
$config['default_host'] = 'ssl://mail.example.com';
$config['default_port'] = 993;
$config['imap_timeout'] = 60;

// SMTP 閰嶇疆锛堥€氳繃 Postfix 鍙戦€侊級
$config['smtp_server'] = 'tls://mail.example.com';
$config['smtp_port'] = 587;
$config['smtp_user'] = '%u';
$config['smtp_password'] = '%p';
$config['smtp_auth_type'] = 'LOGIN';

// 浜у搧鍚嶇О鍜岀晫闈?$config['product_name'] = 'Example Mail - 瀹夊叏閭欢绯荤粺';
$config['skin'] = 'elastic';  // 鐜颁唬 UI 涓婚
$config['temp_dir'] = '/var/lib/roundcube/temp';

// 瀹夊叏璁剧疆
$config['enable_spellcheck'] = true;
$config['spellcheck_engine'] = 'googie';
$config['force_https'] = true;
$config['use_https'] = true;
$config['x_frame_options'] = 'sameorigin';

// 闄勪欢闄愬埗
$config['max_message_size'] = 50 * 1024 * 1024; // 50MB
$config['upload_max_filesize'] = 50 * 1024 * 1024;

// 鎻掍欢
$config['plugins'] = [
    'archive',        // 閭欢褰掓。
    'zipdownload',    // 鎵归噺涓嬭浇
    'markasjunk2',    // 鏍囪鍨冨溇閭欢
    'acl',            // IMAP 璁块棶鎺у埗
    'managesieve'     // 閭欢杩囨护瑙勫垯
];

// 鐢ㄦ埛鐣岄潰涓枃浼樺寲
$config['language'] = 'zh_CN';
$config['date_format'] = 'Y-m-d';
$config['time_format'] = 'H:i';
$config['show_images'] = 1;  // 鑷姩鏄剧ず鍐呭祵鍥剧墖锛堜俊浠诲彂浠朵汉锛?```

### 5.2 Nginx 鍙嶅悜浠ｇ悊閰嶇疆

```nginx
# /etc/nginx/sites-available/roundcube
server {
    listen 80;
    server_name mail.example.com;
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl http2;
    server_name mail.example.com;

    ssl_certificate /etc/letsencrypt/live/mail.example.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/mail.example.com/privkey.pem;
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256;

    root /usr/share/roundcube;
    index index.php index.html;

    # 璁块棶鏃ュ織锛堜笉鍚瘑鐮侊級
    log_format roundcube '$remote_addr - $remote_user [$time_local] '
        '"$request" $status $body_bytes_sent '
        '"$http_referer" "$http_user_agent"';
    access_log /var/log/nginx/roundcube-access.log roundcube;
    error_log /var/log/nginx/roundcube-error.log;

    # PHP-FPM 閰嶇疆
    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php-fpm-roundcube.sock;
        fastcgi_param HTTPS on;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        # 瀹夊叏锛氱姝㈣闂晱鎰熸枃浠?        location ~ /(config|vendor|bin|SQL|README|INSTALL|LICENSE|CHANGELOG|UPGRADING)\.php$ {
            deny all;
        }
    }

    # 闈欐€佽祫婧愮紦瀛?    location ~* ^/(skins|temperate|logs)/.+\.(jpg|jpeg|gif|png|svg|svgz|css|js|woff|woff2)$ {
        expires 30d;
        add_header Cache-Control "public, immutable";
        access_log off;
    }

    # 瀹夊叏锛氶殣钘忕増鏈俊鎭?    location ~ /\. {
        deny all;
        access_log off;
        log_not_found off;
    }

    # Roundcube 鐗规畩璺緞
    location ^~ /installer/ {
        deny all;
    }
}
```

---

## 鍏€侀偖浠跺垪琛ㄦ湇鍔★紙Mailman3锛?
### 6.1 Mailman3 閮ㄧ讲

```yaml
# docker-compose.yml - Mailman3 閭欢鍒楄〃鏈嶅姟
version: '3.8'
services:
  mailman3:
    image: mailman3/mailman3-core:latest
    container_name: mailman3
    environment:
      - HYPERKITTY_API_KEY=${HYPERKITTY_API_KEY}
      - DATABASE_URL=postgresql://mailman:mailman@db/mailman
      - DEFAULT_LANGUAGE=zh_CN
      - MTA_PORT=25
      - MTA_HOST=mail.example.com
    volumes:
      - ./mailman-data:/var/lib/mailman3
      - ./mailman-archives:/var/lib/mailman3/archives
    ports:
      - "8000:8000"  # REST API
    depends_on:
      - db
      - postfix
    restart: unless-stopped

  postorius:
    image: mailman3/postorius:latest
    container_name: postorius
    environment:
      - DATABASE_URL=postgresql://mailman:mailman@db/mailman
      - HYPERKITTY_API_KEY=${HYPERKITTY_API_KEY}
      - SECRET_KEY=${SECRET_KEY}
      - ALLOWED_HOSTS=lists.example.com
    ports:
      - "8001:8000"
    depends_on:
      - mailman3
    restart: unless-stopped

  hyperkitty:
    image: mailman3/hyperkitty:latest
    container_name: hyperkitty
    environment:
      - DATABASE_URL=postgresql://mailman:mailman@db/mailman
      - HYPERKITTY_API_KEY=${HYPERKITTY_API_KEY}
      - SECRET_KEY=${SECRET_KEY}
      - ALLOWED_HOSTS=lists.example.com
    depends_on:
      - mailman3
    restart: unless-stopped

  db:
    image: postgres:15-alpine
    environment:
      POSTGRES_DB: mailman
      POSTGRES_USER: mailman
      POSTGRES_PASSWORD: mailman
    volumes:
      - ./postgres-data:/var/lib/postgresql/data
    restart: unless-stopped

  postfix:
    image: boky/postfix:v110
    container_name: postfix
    environment:
      - HOSTNAME=mail.example.com
      - ALLOWED_SENDER_DOMAINS=example.com
    volumes:
      - ./postfix-spam:/var/spamassassin
    restart: unless-stopped
```

---

## 涓冦€佽嚜鎵樼鍗忎綔閫氫俊濂椾欢

### 7.1 瀹屾暣閫氫俊濂椾欢鏋舵瀯

```
                        鐢ㄦ埛绔?                           鈹?        鈹屸攢鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹尖攢鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹?        鈻?                 鈻?                 鈻?   鈹屸攢鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹?       鈹屸攢鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹?      鈹屸攢鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹?   鈹俁oundcube鈹?       鈹?Mattermost鈹?     鈹?Jitsi   鈹?   鈹?Webmail 鈹?       鈹? 鍥㈤槦鑱婂ぉ  鈹?      鈹?瑙嗛浼氳 鈹?   鈹斺攢鈹€鈹€鈹€鈹攢鈹€鈹€鈹€鈹?       鈹斺攢鈹€鈹€鈹€鈹攢鈹€鈹€鈹€鈹?      鈹斺攢鈹€鈹€鈹€鈹攢鈹€鈹€鈹€鈹?        鈹?                 鈹?                 鈹?        鈻?                 鈻?                 鈻?   鈹屸攢鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹?   鈹?          VPS (Postfix + Mattermost)      鈹?   鈹?                                             鈹?   鈹? MariaDB 鈫愨啋 Dovecot 鈫愨啋 Postfix             鈹?   鈹?        Rspamd 鈫愨啋 ClamAV                  鈹?   鈹斺攢鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹€鈹?```

### 7.2 Mattermost 鑷墭绠″洟闃熻亰澶?
```yaml
# docker-compose.yml - Mattermost 鍥㈤槦鍗忎綔骞冲彴
version: '3.8'
services:
  mattermost:
    image: mattermost/mattermost-enterprise-edition:latest
    container_name: mattermost
    environment:
      - MM_SQLSETTINGS_DRIVERNAME=postgres
      - MM_SQLSETTINGS_DATASOURCE=postgres://mattermost:mmpassword@db:5432/mattermost?sslmode=disable&connect_timeout=10
      - MM_TEAMSETTINGS_SITENAME=Example Team
      - MM_SERVICESETTINGS_SITEURL=https://chat.example.com
      - MM_EMAILSETTINGS_ENABLEEMAILBETHING=true
      - MM_EMAILSETTINGS_SMTPHostname=mail.example.com
      - MM_EMAILSETTINGS_SMTPPort=587
      - MM_EMAILSETTINGS_SMTPUsername=noreply@example.com
      - MM_EMAILSETTINGS_SMTPPassword=${SMTP_PASSWORD}
      - MM_EMAILSETTINGS_SMTPAuth=login
      - MM_EMAILSETTINGS_SMTPUseTLS=true
      - MM_FILESETTINGS_DRIVERTYPE=local
      - MM_FILESETTINGS_DIRECTORY=/mattermost/data
      - MM_LOGSETTINGS_CONSOLELEVEL=INFO
      - MM_LOGSETTINGS_FILELEVEL=DEBUG
    volumes:
      - ./mattermost-data:/mattermost/data
      - ./mattermost-logs:/mattermost/logs
    ports:
      - "8065:8065"
    depends_on:
      - db
    restart: unless-stopped
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:8065/api/v4/system/ping"]
      interval: 30s
      timeout: 10s
      retries: 5

  db:
    image: postgres:15-alpine
    environment:
      POSTGRES_DB: mattermost
      POSTGRES_USER: mattermost
      POSTGRES_PASSWORD: mmpassword
    volumes:
      - ./postgres-mattermost:/var/lib/postgresql/data
    restart: unless-stopped

  jitsi:
    image: jitsi/web:latest
    container_name: jitsi
    environment:
      - PUBLIC_URL=https://meet.example.com
      - DOCKER_HOST_SITE_SHOULD_BE_PUBLIC_URL_SHOULD_BE_SAME=meet.example.com
      - XMPP_AUTH_DOMAIN=auth.meet.example.com
      - XMPP_MUC_DOMAIN=muc.meet.example.com
      - JVB_AUTH_USER=jitsi
    ports:
      - "8000:80"
      - "8443:443"
    volumes:
      - ./jitsi-config:/config
    restart: unless-stopped
```

---

## 鍏€侀偖浠剁洃鎺т笌鏃ュ織鍒嗘瀽

### 8.1 閭欢娴侀噺鐩戞帶浠〃鏉?
```python
#!/usr/bin/env python3
"""
mail-stats.py - 閭欢绯荤粺娴侀噺涓庣姸鎬佺洃鎺?"""
import re
from collections import defaultdict
from datetime import datetime, timedelta
from pathlib import Path

def parse_postfix_log(log_file: str) -> dict:
    """瑙ｆ瀽 Postfix 鏃ュ織锛岃緭鍑虹粺璁?""
    stats = {
        'total_sent': 0,
        'total_received': 0,
        'deferred': 0,
        'bounced': 0,
        'rejected': 0,
        'by_domain': defaultdict(int),
        'by_status': defaultdict(int),
        'slow_deliveries': [],  # 瓒呰繃10绉掔殑鎶曢€?        'errors': []
    }

    log_path = Path(log_file)
    if not log_path.exists():
        return {'error': f'Log file not found: {log_file}'}

    for line in log_path.read_text(errors='ignore').splitlines():
        # 鍙戦€侀偖浠?        if 'status=sent' in line:
            stats['total_sent'] += 1
            match = re.search(r'to=<([^>]+)>', line)
            if match:
                domain = match.group(1).split('@')[-1]
                stats['by_domain'][domain] += 1

        # 鎶曢€掑欢杩?        delay_match = re.search(r'delay=([0-9.]+)', line)
        if delay_match and float(delay_match.group(1)) > 10:
            stats['slow_deliveries'].append({
                'time': line[:15],
                'delay': float(delay_match.group(1))
            })

        # 閫€淇?        if 'status=bounced' in line:
            stats['bounced'] += 1
        if 'status=deferred' in line:
            stats['deferred'] += 1
        if 'status=rejected' in line:
            stats['rejected'] += 1

        # 閿欒
        if 'error' in line.lower() and 'status=' in line:
            stats['errors'].append(line[:100])

    return stats

if __name__ == '__main__':
    import sys
    log_file = sys.argv[1] if len(sys.argv) > 1 else '/var/log/postfix.log'

    print("=== 閭欢绯荤粺鐩戞帶鎶ュ憡 ===")
    print(f"鏃ュ織鏂囦欢: {log_file}")
    print(f"鐢熸垚鏃堕棿: {datetime.now().strftime('%Y-%m-%d %H:%M:%S')}")
    print()

    s = parse_postfix_log(log_file)

    if 'error' in s:
        print(f"[ERROR] {s['error']}")
    else:
        print(f"鍙戦€佹垚鍔? {s['total_sent']:,}")
        print(f"閫€淇? {s['bounced']}")
        print(f"寤惰繜鎶曢€? {s['deferred']}")
        print(f"鎷掓敹: {s['rejected']}")
        print()
        print("--- 鏀朵欢鍩熷悕 TOP 10 ---")
        for domain, count in sorted(s['by_domain'].items(),
                                     key=lambda x: x[1], reverse=True)[:10]:
            print(f"  {count:6d}  {domain}")
        print()
        if s['slow_deliveries']:
            print(f"--- 鎶曢€掑欢杩?>10s 鐨勯偖浠?({len(s['slow_deliveries'])}灏? ---")
            for d in sorted(s['slow_deliveries'],
                           key=lambda x: x['delay'], reverse=True)[:5]:
                print(f"  {d['time']} - 寤惰繜: {d['delay']:.1f}s")
```

### 8.2 鑷姩鍛婅閰嶇疆锛圥rometheus + Alertmanager锛?
```yaml
# mail-alerts.yml - Prometheus 閭欢鏈嶅姟鍛婅瑙勫垯
groups:
  - name: mail-server-alerts
    rules:
      - alert: MailQueueBacklog
        expr: postfix_queue_length > 100
        for: 30m
        labels:
          severity: warning
        annotations:
          summary: "閭欢闃熷垪绉帇涓ラ噸"
          description: "闃熷垪涓湁 {{ $value }} 灏侀偖浠剁瓑寰呮姇閫?

      - alert: HighBounceRate
        expr: rate(postfix_bounced_total[1h]) / rate(postfix_sent_total[1h]) > 0.1
        for: 10m
        labels:
          severity: critical
        annotations:
          summary: "閭欢閫€淇＄巼杩囬珮锛?10%锛?
          description: "褰撳墠閫€淇＄巼 {{ $value | humanizePercentage }}锛屽彲鑳藉奖鍝?IP 淇¤獕"

      - alert: RspamdHighRejectRate
        expr: rate(rspamd_actions_reject[5m]) / rate(rspamd_actions_all[5m]) > 0.3
        for: 15m
        labels:
          severity: warning
        annotations:
          summary: "Rspamd 鎷掔粷鐜囧紓甯?
          description: "30% 浠ヤ笂鐨勯偖浠惰 Rspamd 鎷掔粷锛屽彲鑳介渶瑕佽皟鏁磋鍒?

      - alert: ClamAVDatabaseOld
        expr: time() - clamav_database_timestamp > 86400 * 2
        for: 5m
        labels:
          severity: warning
        annotations:
          summary: "ClamAV 鐥呮瘨搴撹繃鏈?
          description: "鐥呮瘨搴撳凡鏈?{{ $value | humanizeDuration }} 鏈洿鏂?
```

---

## 涔濄€侀偖浠剁郴缁熻繍缁磋剼鏈笌宸ュ叿绠?
### 9.1 涓€閿儴缃茶剼鏈?
```bash
#!/bin/bash
# deploy-mailserver.sh - 涓€閿儴缃插畬鏁撮偖浠剁郴缁?# 閫傜敤浜?Ubuntu 22.04 LTS / Debian 12

set -e

echo "=== VPS 閭欢鏈嶅姟鍣ㄤ竴閿儴缃?==="
echo "璀﹀憡锛氭鑴氭湰灏嗕慨鏀圭郴缁熼厤缃紝璇峰湪骞插噣鐨勭郴缁熶笂杩愯"
read -p "缁х画锛?(y/N): " confirm
[ "$confirm" != "y" ] && exit 1

DOMAIN=$1
if [ -z "$DOMAIN" ]; then
    read -p "璇疯緭鍏ラ偖浠跺煙鍚嶏紙濡?example.com锛? " DOMAIN
fi

# ===== 姝ラ 1锛氱郴缁熼厤缃?=====
echo "[1/8] 閰嶇疆涓绘満鍚?.."
hostnamectl set-hostname "mail.${DOMAIN}"
echo "mail.${DOMAIN}" >> /etc/hosts

# ===== 姝ラ 2锛氬畨瑁呰蒋浠跺寘 =====
echo "[2/8] 瀹夎杞欢鍖?.."
apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    postfix postfix-mysql dovecot-core dovecot-imapd dovecot-lmtpd dovecot-mysql \
    dovecot-solr mariadb-server clamav clamav-daemon rspamd \
    roundcube roundcube-mysql certbot python3-certbot-nginx \
    fail2ban net-tools dnsutils opendkim opendkim-tools

# ===== 姝ラ 3锛歁ySQL 鏁版嵁搴?=====
echo "[3/8] 閰嶇疆鏁版嵁搴?.."
mysql -e "CREATE DATABASE IF NOT EXISTS mailserver CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;"
mysql -e "CREATE USER IF NOT EXISTS 'mailuser'@'localhost' IDENTIFIED BY 'CHANGE_ME';"
mysql -e "GRANT SELECT ON mailserver.* TO 'mailuser'@'localhost';"
mysql -e "FLUSH PRIVILEGES;"

# ===== 姝ラ 4锛歅ostfix 閰嶇疆 =====
echo "[4/8] 閰嶇疆 Postfix..."
postconf -e "myhostname = mail.${DOMAIN}"
postconf -e "mydomain = ${DOMAIN}"
postconf -e "virtual_alias_maps = mysql:/etc/postfix/mysql/virtual_alias_maps.cf"
postconf -e "virtual_mailbox_maps = mysql:/etc/postfix/mysql/virtual_mailbox_maps.cf"
postconf -e "virtual_transport = lmtp:unix:private/dovecot-lmtp"

# ===== 姝ラ 5锛欴ovecot 閰嶇疆 =====
echo "[5/8] 閰嶇疆 Dovecot..."
# Dovecot SQL 閰嶇疆宸插湪涓婃枃閰嶇疆

# ===== 姝ラ 6锛歋SL 璇佷功 =====
echo "[6/8] 鐢宠 SSL 璇佷功..."
certbot certonly --standalone -d "mail.${DOMAIN}" --non-interactive --agree-tos -m "admin@${DOMAIN}"

# ===== 姝ラ 7锛氶偖浠惰璇?=====
echo "[7/8] 閰嶇疆 SPF / DKIM / DMARC..."
# SPF 宸查厤缃湪 DNS 涓?# DKIM 瀵嗛挜鐢熸垚鍦ㄦ楠?3.3
echo "璇锋墜鍔ㄩ厤缃?DNS 璁板綍锛堝弬鑰?README锛?
echo "DKIM 鍏挜: mail._domainkey.${DOMAIN}"

# ===== 姝ラ 8锛氬惎鍔ㄦ湇鍔?=====
echo "[8/8] 鍚姩鏈嶅姟..."
systemctl enable --now postfix dovecot mariadb rspamd fail2ban

echo ""
echo "=== 閮ㄧ讲瀹屾垚 ==="
echo "Webmail: https://mail.${DOMAIN}/roundcube"
echo "涓嬩竴姝ワ細璇烽厤缃?DNS SPF / DKIM / DMARC 璁板綍锛堣 README锛?
```

### 9.2 閭欢鍋ュ悍妫€鏌ヨ剼鏈?
```bash
#!/bin/bash
# mail-health-check.sh - 姣忔棩閭欢绯荤粺鍋ュ悍妫€鏌?
echo "=== 閭欢绯荤粺鍋ュ悍妫€鏌?$(date) ==="
echo ""

# 1. 鏈嶅姟鐘舵€?echo "--- 鏈嶅姟鐘舵€?---"
for svc in postfix dovecot mariadb rspamd clamav-daemon; do
    if systemctl is-active --quiet $svc; then
        echo "  鉁?$svc: 杩愯涓?
    else
        echo "  鉂?$svc: 鏈繍琛?
    fi
done

# 2. 閭欢闃熷垪
echo ""
echo "--- 閭欢闃熷垪 ---"
QUEUE_SIZE=$(mailq 2>/dev/null | grep -c "^[A-F0-9]" || echo "0")
echo "  褰撳墠闃熷垪: $QUEUE_SIZE 灏?
if [ "$QUEUE_SIZE" -gt 100 ]; then
    echo "  鈿狅笍  璀﹀憡锛氶槦鍒楃Н鍘嬭秴杩?100 灏?
fi

# 3. DNS 璁板綍楠岃瘉
echo ""
echo "--- DNS 璁板綍楠岃瘉 ---"
for record_type in A MX SPF DKIM DMARC; do
    case $record_type in
        MX)
            result=$(dig +short MX example.com 2>/dev/null | grep "mail.example.com" || echo "")
            ;;
        SPF)
            result=$(dig +short TXT example.com 2>/dev/null | grep "v=spf1" || echo "")
            ;;
        DKIM)
            result=$(dig +short TXT mail._domainkey.example.com 2>/dev/null | grep "v=DKIM1" || echo "")
            ;;
        DMARC)
            result=$(dig +short TXT _dmarc.example.com 2>/dev/null | grep "v=DMARC1" || echo "")
            ;;
    esac
    if [ -n "$result" ]; then
        echo "  鉁?$record_type: 宸查厤缃?
    else
        echo "  鉂?$record_type: 鏈厤缃?
    fi
done

# 4. SSL 璇佷功鏈夋晥鏈?echo ""
echo "--- SSL 璇佷功 ---"
EXPIRY=$(openssl x509 -in /etc/letsencrypt/live/mail.example.com/fullchain.pem -noout -enddate 2>/dev/null | cut -d= -f2)
echo "  鍒版湡鏃堕棿: $EXPIRY"

# 5. Rspamd 缁熻
echo ""
echo "--- Rspamd 缁熻 ---"
redis-cli -n 1 SCAN 0 MATCH "rspamd*" COUNT 5 | head -5 || echo "  Rspamd 姝ｅ父"
```

---

## 鍗併€佸父瑙侀棶棰樹笌鏁呴殰鎺掓煡

### 10.1 閭欢鍙戦€佽鎷掓敹鐨勬帓鏌ユ祦绋?
```
閭欢鍙戦€佸け璐ワ紙Gmail/Outlook 鎷掓敹锛?       鈹?       鈻?Step 1: 妫€鏌?IP 淇¤獕
  鈫?https://mxtoolbox.com/blacklists.aspx
  鈫?https://intodns.com/your-domain.com
  鈫?IP 琚垪鍏ラ粦鍚嶅崟 鈫?鐢宠绉婚櫎鎴栨洿鎹?IP

Step 2: 妫€鏌?DNS 璁板綍
  鈫?SPF: dig +short TXT your-domain.com
  鈫?DKIM: dig +short TXT mail._domainkey.your-domain.com
  鈫?DMARC: dig +short TXT _dmarc.your-domain.com
  鈫?MX: dig +short MX your-domain.com
  鈫?浠讳綍缂哄け 鈫?绔嬪嵆閰嶇疆

Step 3: 妫€鏌ラ偖浠跺唴瀹?  鈫?SpamAssassin 鍦ㄧ嚎妫€娴?  鈫?鍘婚櫎杩囧害钀ラ攢鐢ㄨ
  鈫?鍑忓皯閾炬帴鏁伴噺

Step 4: 棰勭儹鏂?IP
  鈫?浠庡皯閲忛偖浠跺紑濮嬶紙姣忓ぉ 50-100 灏侊級
  鈫?閫愭澧炲姞鍙戦€侀噺
  鈫?浣跨敤涓撳睘鍙戦€?IP 涓庢敹浠?IP 鍒嗙
```

### 10.2 閭欢闂閫熸煡琛?
| 鐥囩姸 | 鍘熷洜 | 瑙ｅ喅鏂规 |
|------|------|---------|
| 閭欢鍙戜笉鍑猴紙杩炴帴瓒呮椂锛?| VPS 灏佺绔彛 25 | 鑱旂郴 IDC 瑙ｅ皝鎴栦娇鐢?587 绔彛 |
| Gmail 鎷掓敹锛?50-5.7.1锛?| IP/鍩熷悕淇¤獕浣?| 棰勭儹 IP + 閰嶇疆瀹屾暣璁よ瘉 |
| Outlook 鎷掓敹锛?50 5.7.606锛墊 缂哄皯 DKIM/SPF | 閰嶇疆瀹屾暣涓夎璇?|
| 鏀朵笉鍒伴偖浠?| MX 璁板綍閿欒 | 妫€鏌?DNS MX 鎸囧悜 |
| 鍙戦€佹參锛堝欢杩?>30s锛?| DNS 鏌ヨ鎱?RBL 鏌ヨ | 閰嶇疆 DNS 缂撳瓨锛屾坊鍔?ignore_mx_lookup |
| Roundcube 鏃犳硶鐧诲綍 | 鏁版嵁搴撹繛鎺ラ敊璇?| 妫€鏌?config.inc.php 鏁版嵁搴?DSN |
| 闄勪欢鍙戦€佸け璐?| 鏂囦欢杩囧ぇ | 妫€鏌?message_size_limit |

### 10.3 閭欢绯荤粺杩佺Щ鏂规

```bash
#!/bin/bash
# migrate-mail.sh - 閭欢璐︽埛杩佺Щ鑴氭湰
# 浠庢棫鏈嶅姟鍣ㄨ縼绉荤敤鎴峰拰閭欢鍒版柊鏈嶅姟鍣?
OLD_SERVER="oldmail.example.com"
NEW_SERVER="mail.example.com"
MIGRATE_USERS=("user1@example.com" "user2@example.com" "admin@example.com")

for user in "${MIGRATE_USERS[@]}"; do
    echo "杩佺Щ: $user"
    # IMAP 鍚屾锛堜娇鐢?imapsync锛?    imapsync \
        --host1 "$OLD_SERVER" --user1 "$user" --password1 "OLD_PASS" \
        --host2 "$NEW_SERVER" --user2 "$user" --password2 "NEW_PASS" \
        --tls1 --tls2 \
        --automap \
        --subscribe \
        --syncinternaldates \
        --exclude "\All Mail" \
        --noexpungeafter
    echo "鉁?$user 杩佺Щ瀹屾垚"
done
echo "鎵€鏈夌敤鎴疯縼绉诲畬鎴?
```

---

## 馃敆 鎺ㄥ箍鍏ュ彛

**銆怌lashVIP 鏈哄満鎺ㄨ崘銆?*锛歔https://nav.clashvip.net](https://nav.clashvip.net) | [https://clashvip.net](https://clashvip.net)  
**銆怴PS 浼樻儬鎺ㄨ崘銆?*锛歔https://vpsvip.net](https://vpsvip.net)  
**銆怌lash for Windows 瀹㈡埛绔€?*锛歔https://clash-for-windows.net](https://clash-for-windows.net)  
**銆怌lashHub 绀惧尯銆?*锛歔https://bbs.clashhub.net](https://bbs.clashhub.net) | [https://clashhub.net](https://clashhub.net)

---

> 馃搮 鏈€鍚庢洿鏂帮細2026-09-24 | 瑙夊緱鏈夌敤锛熻缁欎粨搴撲竴涓?猸? 
> 鈿欙笍 鏈粨搴撴兜鐩?VPS 閭欢鏈嶅姟鍣ㄨ嚜寤恒€侀偖浠惰璇侀厤缃笌瀹夊叏闃叉姢鍏ㄦ祦绋嬨€?
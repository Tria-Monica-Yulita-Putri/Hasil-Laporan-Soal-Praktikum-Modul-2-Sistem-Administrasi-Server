# **HASIL LAPORAN SOAL PRAKTIKUM MODUL 2 SISTEM ADMINISTRASI SERVER**

1. Pertama-tama rubah LXC landing dengan ubuntu focal (destroy n create, same ip, same name)

   ```markdown
   lxc-ls -f
   ```

   ```markdown
   rm /var/lib/lxc/ubuntu_landing/lxc_snapshots
   lxc-destroy ubuntu_landing
   ```

   

   ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\1.png)

   

   * Lalu, langkah selanjutnya yaitu create ubuntu_landing

     ```markdown
     sudo lxc-create -n ubuntu_landing -t download -- --dist ubuntu --release focal --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\2.png)

     

   * Setelah create ubuntu_landing, maka langkah selanjutnya yaitu mencoba menjalankan ubuntu_landing atau start ubuntu_landing. Setelah ubuntu_landing berhasil dijalankan, maka langkah selanjutnya yaitu instal net-tools

     ```markdown
     lxc-start ubuntu_landing
     ```

     ```markdown
     lxc-attach ubuntu_landing
     ```

     ```markdown
     apt install nano net-tools curl
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\3.png)

     

   * Setelah instal nano net-tools berhasil, maka langkah selanjutnya yaitu atur IP

     ```markdown
     nano /etc/netplan/10-lxc.yaml
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\4.png)

     

   * Setelah mengatur IP, maka langkah selanjutnya yaitu mengganti IP

     ```markdown
     netplan apply
     ```

     ```markdown
     ip r
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\5.png)

     

   * Setelah IP berhasil diganti, maka langkah selanjutnya yaitu instal ssh pada server

     ```markdown
     apt install openssh-server python -y
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\6.png)

     

   * Setelah berhasil install ssh, maka langkah berikutnya yaitu masuk sshd_config untuk mengatur permit login 

     ```markdown
     nano sshd_config
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\7.png)

     

   * Setelah mengatur permit login di sshd_config, maka langkah selanjutnya yaitu setting password ssh 

     ``` markdown
     passwd
     ```

     ```markdown
     exit
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\8.png)

     

   * Setelah mengubah dan mengatur permit login di sshd_config dan berhasil setting password ssh, maka langkah selanjutnya yaitu mencoba masuk di ssh yang baru dan dapat dilihat bahwa bisa login dengan host yang baru yaitu 10.0.3.103

     ```markdown
     ssh root@10.0.3.103
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\9.png)

     

     

2. Setelah merubah LXC landing dengan ubuntu focal, maka selanjutnya yaitu merubah LXC php7 dengan ubuntu focal (destroy n create, same ip, same name)

   ```markdown
   lxc-ls -f
   ```

   ```markdown
   rm /var/lib/lxc/ubuntu_php7.4/lxc_snapshots
   ```

   ```markdown
   lxc-destroy ubuntu_php7.4 -f
   ```

   ```markdown
   lxc-ls -f
   ```

   

   ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\10.png)

   

   * Lalu, langkah selanjutnya yaitu membuat dan mendownload ubuntu_php7.4

     ```markdown
     sudo lxc-create -n ubuntu_php7.4 -t download -- --dist ubuntu --release focal --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\11.png)

     

   * Setelah berhasil membuat dan mendownload ubuntu_php7.4 maka langkah selanjutnya yaitu jalankan ubuntu_php7.4 

     ```markdown
     lxc-start ubuntu_php7.4
     ```

     ```markdown
     lxc-attach ubuntu_php7.4
     ```

     

   * Setelah berhasil membuat dan menjalankan ubuntu_php7.4, maka step selanjutnya yaitu install net-tools

     ```markdown
     apt install nano net-tools curl
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\12.png)

     

   * Setelah install net-tools berhasil, maka step selanjutnya yaitu merubah IP Address ubuntu_php7.4 

     ```markdown
     nano /etc/netplan/10-lxc.yaml
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\13.png)

     

   * Setelah berhasil merubah IP Address ubuntu_php7.4, lalu step selanjutnya yaitu mengapply IP ubuntuphp7 lalu coba menampilkan IP root nya

     ```markdown
     netplan apply
     ```

     ```markdown
     ip r
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\14.png)

     

   * Setelah berhasil merubah dan ditampilkan IP root nya, maka langkah selanjutnya yaitu install openssh server

     ```markdown
     apt install openssh-server python -y
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\15.png)

     

   * Setelah berhasil menginstall openssh server, maka langkah selanjutnya yaitu mengedit sshd_config 

     ```markdown
     cd /etc/ssh
     ```

     ```markdown
     nano sshd_config
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\16.png)

     

   * Setelah berhasil mengedit sshd_config, lalu langkah selanjutnya yaitu restart ssh dan type the new password 

     ```markdown
     service sshd restart
     ```

     ```markdown
     passwd
     exit
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\17.png)

     

   * Setelah berhasil restart sshd dan type the new password, maka step selanjutnya yaitu mencoba connect ke ssh 10.0.3.101

     ```markdown
     ssh root@10.0.3.101
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\18.png)

     

3. vm.local/

   * Pertama-tama yaitu membuat directory laravel 8 pada lxc_landing

     ```markdown
     mkdir laravel
     ```

     ```markdown
     cd laravel/
     ```

     
     
     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\19.png)

     

   * Setelah membuat directory laravel 8, maka langkah selanjutnya yaitu mengatur konfigurasi ansible di nano hosts dan nano nginxphp.yml

     ```markdown
     nano hosts
     ```

     ```markdown
     [landing]
     ubuntu_landing ansible_host=lxc_landing.dev ansible_ssh_user=root ansible_become_pass=1234
     ```
     
     
     
     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\20.png)
     
     
     
     ```markdown
     nano nginxphp.yml
     ```
     
      ```markdown
      ---
      - hosts: all
        become : yes
        tasks:
          - name: install nginx nginx extras
            apt:
             pkg:
               - nginx
               - nginx-extras
             state: latest
          - name: start nginx
            service:
             name: nginx
             state: started
          - name: menginstall tools
            apt:
             pkg:
               - curl
               - software-properties-common
               - unzip
             state: latest
          - name: "Repo PHP 7.4"
            apt_repository:
              repo="ppa:ondrej/php"
          - name: "Updating the repo"
            apt: update_cache=yes
          - name: Installation PHP 7.4
            apt: name=php7.4 state=present
          - name: install php untuk laravel
            apt:
             pkg:
                - php7.4-fpm
                - php7.4-mysql
                - php7.4-mbstring
                - php7.4-xml
                - php7.4-bcmath
                - php7.4-json
                - php7.4-zip
                - php7.4-common
             state: present
      ```
     
     
     
     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\21.png)
     
     

   * Setelah berhasil di konfigurasi, maka langkah selanjutnya yaitu mencoba untuk menjalankan ansible playbook nginxphp.yml

     ```markdown
     ansible-playbook -i hosts nginxphp.yml -k
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\22.png)

     

   * Setelah berhasil dijalankan, maka step selanjutnya yaitu membuat file installcomposer.yml

     ```markdown
     nano installcomposer.yml
     ```

     ```markdown
     ---
      -hosts: all
       become : yes
       tasks:
        - name: Download and install Composer
          shell: curl -sS https://getcomposer.org/installer | php
          args:
           chdir: /usr/src/
           creates: /usr/local/bin/composer
           warn: false
        - name: Add Composer to global path
          copy:
           dest: /usr/local/bin/composer
           group: root
           mode: '0755'
           owner: root
           src: /usr/src/composer.phar
           remote_src: yes
        - name: Composer create project
          become_user: root
          composer:
           command: create-project
           arguments: laravel/laravel landing 
           working_dir: /var/www/html
           prefer_dist: yes
          environment:
             COMPOSER_NO_INTERACTION: "1"
        - name: mengkopi file .env.example jadi .env
          copy:
           dest: /var/www/html/landing/.env.example
           src: /var/www/html/landing/.env
           remote_src: yes
        - name: mengganti konfigurasi .env
          lineinfile:
           path: /var/www/html/landing/.env
           regexp: "{{ item.regexp }}"
           line: "{{ item.line }}"
           backrefs: yes
          loop:
           - { regexp: '^(.)DB_HOST(.)$', line: 'DB_HOST=10.0.3.200' }
           - { regexp: '^(.)DB_DATABASE(.)$', line: 'DB_DATABASE=landing' }
           - { regexp: '^(.)DB_USERNAME(.)$', line: 'DB_USERNAME=admin' }
           - { regexp: '^(.)DB_PASSWORD(.)$', line: 'DB_PASSWORD= ' }
           - { regexp: '^(.)APP_URL(.)$', line: 'APP_URL=http://vm.local' }
           - { regexp: '^(.)APP_NAME=(.)$', line: 'APP_NAME=landing' }
        - name: Composer install ke landing
          composer:
            command: install
            working_dir: /var/www/html/landing
          environment:
            COMPOSER_NO_INTERACTION: "1"
        - name: generate php artisan
          args:
           chdir: /var/www/html/landing
          shell: php artisan key:generate
        - name: mengganti permission storage
          file:
           path: /var/www/html/landing/storage
           mode: 0777
           recurse: yes
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\23.png)

     

   * Setelah membuat file install composer.yml, maka langkah selanjutnya yaitu menjalankan ansible playbook installcomposer.yml

     ```markdown
     ansible-playbook -i hosts installcomposer.yml -k
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\24.png)

     

   * Setelah berhasil dijalankan, maka langkah selanjutnya yaitu setting lxc_landing.dev

     ```markdown
     nano lxc_landing.dev
     ```

     ```markdown
     server {
             listen 80;
     
             root /var/www/html/landing/public;
             index index.php index.html index.htm;
             server_name lxc_landing.dev;
     
             error_log /var/log/nginx/landing_error.log;
             access_log /var/log/nginx/landing_access.log;
     
             client_max_body_size 100M;
             location / {
                     try_files $uri $uri/ /index.php$args;
             }
             location ~\.php$ {
                     include snippets/fastcgi-php.conf;
                     fastcgi_pass unix:run/php/php7.4-fpm.sock;
                     fastcgi_param SCRIPTFILENAME $document_root$fastcgi_script_name;
             }
     }
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\25.png)

     

   * Setelah setting lxc_landing dilakukan, maka step selanjutnya yaitu setting config.yml

     ```markdown
     nano config.yml
     ```

     ```markdown
     ---
     - hosts: all
       become : yes
       vars:
         domain: 'lxc_landing.dev'
       tasks:
        - name: stop apache2
          service:
           name: apache2
           state: stopped
           enabled: no
        - name: Write {{ domain }} to /etc/hosts
          lineinfile:
           dest: /etc/hosts
           regexp: '.*{{ domain }}$'
           line: "127.0.0.1 {{ domain }}"
           state: present
        - name: ensure nginx is at the latest version
          apt: name=nginx state=latest
        - name: start nginx
          service:
           name: nginx
           state: started
        - name: copy the nginx config file 
          copy:
           src: ~/ansible/laravel/lxc_landing.dev
           dest: /etc/nginx/sites-available/lxc_landing.dev
        - name: Symlink lxc_landing.dev
          command: ln -sfn /etc/nginx/sites-available/lxc_landing.dev /etc/nginx/sites-enabled/lxc_landing.dev
          args:
           warn: false
        - name: restart nginx
          service:
           name: nginx
           state: restarted
        - name: restart php7
          service:
           name: php7.4-fpm
           state: restarted
        - name: curl web
          command: curl -i http://lxc_landing.dev
          args:
           warn: false
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\26.png)

     

   * Setelah setting config.yml, maka langkah selanajutnya yaitu coba memanggil config.yml

     ```markdown
      ansible-playbook -i hosts config.yml -k
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\27.png)

     

   * Setelah berhasil dijalankan, maka langkah step selanjutnya yaitu mengakses url vm.local

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\28.png)

     

4. vm.local/blog

   * Pertama-tama membuat directory wordpress terbaru pada ansible

     ```markdown
     cd ~/ansible/
     ```

     ```markdown
     mkdir wordpress
     ```

     ```markdown
     cd wordpress/
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\29.png)

     

   * Setelah berhasil install, maka langkah selanjutnya yaitu masuk dan setting wordpress nano host 
   
     ```markdown
     nano hosts
     ```

     

     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\30.png)

     

   * Setelah setting wordpress nano hosts, maka step selanjutnya yaitu setting nano installwordpress.yml
   
     ```markdown
     nano installwordpress.yml
     ```

     ```markdown
     ---
     - hosts: all
       vars:
         domain: 'lxc_php7.dev'
       tasks:
        - name: delete apt chache
          become: yes
          become_user: root
          become_method: su
          command: rm -vf /var/lib/apt/lists/*
     
        - name: install requirement
          become: yes
          become_user: root
          become_method: su
          apt: name={{ item }} state=latest update_cache=true
          with_items:
           - nginx
           - nginx-extras
           - curl
           - wget
           - php7.4
           - php7.4-fpm
           - php7.4-curl
           - php7.4-xml
           - php7.4-gd
           - php7.4-opcache
           - php7.4-mbstring
           - php7.4-zip
           - php7.4-json
           - php7.4-cli
           - php7.4-mysqlnd
           - php7.4-xmlrpc
           - php7.4-curl
     
        - name: wget wordpress
          shell: wget -c http://wordpress.org/latest.tar.gz
     
        - name: tar latest.tar.gz
          shell: tar -xvzf latest.tar.gz
     
        - name: copy folder wordpress
          shell: cp -R wordpress /var/www/html/blog
     
        - name: chmod
          become: yes
          become_user: root
          become_method: su
          command: chmod 775 -R /var/www/html/blog/
     
        - name: copy .wp-config.conf
          copy:
           src=~/ansible/wordpress/wp.conf
           dest=/var/www/html/blog/wp-config.php
     
        - name: copy wordpress.conf
          copy:
           src=~/ansible/wordpress/wordpress.conf
           dest=/etc/nginx/sites-available/{{ domain }}
          vars:
           servername: '{{ domain }}'
     
        - name: Symlink wordpress.conf
          command: ln -sfn /etc/nginx/sites-available/{{ domain }} /etc/nginx/sites-enabled/{{ domain }}
        
        - name: restart nginx
          become: yes
          become_user: root
          become_method: su
          action: service name=nginx state=restarted
     
        - name: Write {{ domain }} to /etc/hosts
          lineinfile:
           dest: /etc/hosts
           regexp: '.*{{ domain }}$'
           line: "127.0.0.1 {{ domain }}"
           state: present
     
        - name: enable module php mbstring
          command: phpenmod mbstring
     
        - name: restart php
          become: yes
          become_user: root
          become_method: su
          action: service name=php7.4-fpm state=restarted
     
        - name: restart nginx
          become: yes
          become_user: root
          become_method: su
          action: service name=nginx state=restarted
     ```
   
     
   
     
   
     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\31.png)
   
     
   
   * Lalu, langkah selanjutnya yaitu setting nano wp.conf
   
     ```markdown
     nano wp.conf
     ```
   
     ```markdown
     <?php
     /**
      * The base configuration for WordPress
      *
      * The wp-config.php creation script uses this file during the installation.
      * You don't have to use the web site, you can copy this file to "wp-config.php"
      * and fill in the values.
      *
      * This file contains the following configurations:
      *
      * * MySQL settings
      * * Secret keys
      * * Database table prefix
      * * ABSPATH
      *
      * @link https://wordpress.org/support/article/editing-wp-config-php/
      *
      * @package WordPress
      */
     
     define( 'WP_HOME', 'http://vm.local/blog' );
     define( 'WP_SITEURL', 'http://vm.local/blog' );
     
     // * MySQL settings - You can get this info from your web host * //
     /** The name of the database for WordPress */
     define( 'DB_NAME', 'blog' );
     
     /** MySQL database username */
     define( 'DB_USER', 'admin' );
     
     /** MySQL database password */
     define( 'DB_PASSWORD', 'SysAdminSas0102' );
     
     /** MySQL hostname */
     define( 'DB_HOST', '10.0.3.200:3306' );
     
     /** Database charset to use in creating database tables. */
     define( 'DB_CHARSET', 'utf8' );
     
     /** The database collate type. Don't change this if in doubt. */
     define( 'DB_COLLATE', '' );
     
     /**#@+
      * Authentication unique keys and salts.
      *
      * Change these to different unique phrases! You can generate these using
      * the {@link https://api.wordpress.org/secret-key/1.1/salt/ WordPress.org secret-key service}.
      *
      * You can change these at any point in time to invalidate all existing cookies.
      * This will force all users to have to log in again.
      *
      * @since 2.6.0
      */
     define( 'AUTH_KEY',         'put your unique phrase here' );
     define( 'SECURE_AUTH_KEY',  'put your unique phrase here' );
     define( 'LOGGED_IN_KEY',    'put your unique phrase here' );
     define( 'NONCE_KEY',        'put your unique phrase here' );
     define( 'AUTH_SALT',        'put your unique phrase here' );
     define( 'SECURE_AUTH_SALT', 'put your unique phrase here' );
     define( 'LOGGED_IN_SALT',   'put your unique phrase here' );
     define( 'NONCE_SALT',       'put your unique phrase here' );
     
     /*#@-/
     
     /**
      * WordPress database table prefix.
      *
      * You can have multiple installations in one database if you give each
      * a unique prefix. Only numbers, letters, and underscores please!
      */
     $table_prefix = 'wp_';
     
     /**
      * For developers: WordPress debugging mode.
      *
      * Change this to true to enable the display of notices during development.
      * It is strongly recommended that plugin and theme developers use WP_DEBUG
      * in their development environments.
      *
      * For information on other constants that can be used for debugging,
      * visit the documentation.
      *
      * @link https://wordpress.org/support/article/debugging-in-wordpress/
      */
     define( 'WP_DEBUG', false );
     
     /* Add any custom values between this line and the "stop editing" line. */
     
     
     
     /* That's all, stop editing! Happy publishing. */
     
     /** Absolute path to the WordPress directory. */
     if ( ! defined( 'ABSPATH' ) ) {
             define( 'ABSPATH', _DIR_ . '/' );
     }
     
     /** Sets up WordPress vars and included files. */
     require_once ABSPATH . 'wp-settings.php';
     ```
   
     
   
     
   
     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\33.png)
   
     
   
   * Setelah setting di nano wp.conf, maka langkah selanjutnya yaitu setting di nano wordpress.conf
   
     ```markdown
     nano wordpress.conf
     ```
   
     ```markdown
     server {
          listen 80;
          listen [::]:80;
     
          # Log files for Debugging
          access_log /var/log/nginx/wordpress-access.log;
          error_log /var/log/nginx/wordpress-error.log;
     
          # Webroot Directory for Laravel project
          root /var/www/html/blog;
          index index.php index.html index.htm;
     
          # Your  Name
          server_name lxc_php7.dev;
     
          location / {
                  try_files $uri $uri/ /index.php?$query_string;
          }
     
          # PHP-FPM Configuration Nginx
          location ~ \.php$ {
                  try_files $uri =404;
                  fastcgi_split_path_info ^(.+\.php)(/.+)$;
                  fastcgi_pass unix:/run/php/php7.4-fpm.sock;
                  fastcgi_index index.php;
                  fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
                  include fastcgi_params;
          }
     }
     ```
   
     
   
     
   
     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\34.png)
   
     
   
   * Setelah setting di nano wordpress.conf, maka step selanjutnya yaitu mencoba memanggil hosts installwordpress.yml 
   
     ```markdown
     sudo ansible-playbook -i hosts installwordpress.yml -k
     ```
   
     
   
     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\35.png)
   
     
   
   * Setelah ansible playbook installwordpress.yml berhasil dijalankan, maka step terakhir yaitu akses url vm.local/blog 
   
     
   
     ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\36.png)
   
     
   
     * Coba sign in atau membuat akun wordpress yang berisi title (judul), username dan juga password
   
       
   
       ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\37.png)
   
     
   
     * Setelah membuat akun, maka tampilan akan seperti gambar dibawah ini, yang berarti sudah sukses membuat akun wordpress dengan username admin
   
       
   
       ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\38.png)
   
     
   
     * Setelah itu kita coba login wordpress dengan username dan password yang sudah dibuat tadi
   
       
       
       ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\39.png)
   
     
   
     * Setelah login, maka akan terdapat tampilan dashboard wordpress seperti gambar dibawah ini
   
       
   
       ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\40.png)
   
     
   
     * Setelah berhasil masuk ke dashboard wordpress, maka coba refresh vm.local/blog, dan akan muncul tampilan seperti gambar dibawah ini
   
       
   
       ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\41.png)
     



## **SOAL TAMBAHAN**

- Rubah konfigurasi php7.4 yang semula menggunakan socket menjadi menggunakan port (127.0.0.1:9001) 

  ##### **Untuk vm.local (laravel)**

  * Pertama-tama masuk ke nano lxc_landing.dev untuk mengubah konfigurasi di dalam nano lxc_landing.dev dengan port 127.0.0.1:9001

    ```markdown
    nano lxc_landing.dev
    ```

    

    ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\42.png)

    

    ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\43.png)

    

  * Setelah merubah konfigurasu di dalam lxc_landing.dev, maka langkah selanjutnya yaitu membuat file dengan memberikan nama tambahan1.yml. Setelah itu masuk ke file tambahan1.yml yang sudah dibuat tadi untuk mengganti `listen nya menjadi 127.0.0.1:9001

    ```markdown
    nano tambahan1.yml
    ```

    ```markdown
    ---
    - hosts: all
      become : yes
      tasks:
       - name: mengganti php sock
         lineinfile:
          path: /etc/php/7.4/fpm/pool.d/www.conf
          regexp: '^(.*)listen =(.*)$'
          line: 'listen = 127.0.0.1:9001'
          backrefs: yes
       - name: copy the nginx config file 
         copy:
          src: ~/ansible/laravel/lxc_landing.dev
          dest: /etc/nginx/sites-available/lxc_landing.dev
       - name: Symlink lxc_landing.dev
         command: ln -sfn /etc/nginx/sites-available/lxc_landing.dev /etc/nginx/sites-enabled/lxc_landing.dev
         args:
          warn: false
       - name: restart nginx
         service:
          name: nginx
          state: restarted
       - name: restart php7
         service:
          name: php7.4-fpm
          state: restarted
       - name: curl web
         command: curl -i http://lxc_landing.dev
         args:
          warn: false
    ```

    

    

    ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\44.png)

    

    ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\45.png)

    

  * Setelah berhasil diganti, maka langkah selanjutnya yaitu mencoba menjalankan ansible playbook hosts tambahan1.yml

    ```markdown
    ansible-playbook -i hosts tambahan1.yml -k
    ```

    

    ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\46.png)

    

  * Setelah berhasil menjalankan ansible playbook hosts tambahan1.yml, maka langkah selanjutnya yaitu mengakses url vm.local

    

    ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\47.png)

    

  **Untuk vm.local/blog (wordpress)**

  * Pertama-tama masuk ke nano wordpress.conf untuk mengubah konfigurasi di dalam nano wordpress.conf  dengan port 127.0.0.1:9001

    ```markdown
    nano wordpress.conf
    ```

    

    ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\48.png)

    

    ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\49.png)

    

  * Setelah merubah konfigurasi di dalam wordpress.conf , maka langkah selanjutnya yaitu membuat file dengan memberikan nama tambahan1.yml. Setelah itu masuk ke file tambahan1.yml yang sudah dibuat tadi untuk mengganti `listen nya menjadi 127.0.0.1:9001

    ```markdown
    nano tambahan1.yml
    ```

    ```markdown
    ---
    - hosts: all
      become : yes
      tasks:
       - name: mengganti php sock
         lineinfile:
          path: /etc/php/7.4/fpm/pool.d/www.conf
          regexp: '^(.*)listen =(.*)$'
          line: 'listen = 127.0.0.1:9001'
          backrefs: yes
       - name: copy the nginx config file 
         copy:
          src: ~/ansible/wordpress/wordpress.conf
          dest: /etc/nginx/sites-available/lxc_php7.dev
       - name: Symlink lxc_php7.dev
         command: ln -sfn /etc/nginx/sites-available/lxc_php7.dev /etc/nginx/sites-enabled/lxc_php7.dev
         args:
          warn: false
       - name: restart nginx
         service:
          name: nginx
          state: restarted
       - name: restart php7
         service:
          name: php7.4-fpm
          state: restarted
       - name: curl web
         command: curl -i http://lxc_php7.dev
         args:
          warn: false
    ```

    

    

    ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\50.png)

    

    ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\51.png)

    

  * Setelah berhasil diganti, maka langkah selanjutnya yaitu mencoba menjalankan ansible playbook hosts tambahan1.yml

    ```markdown
    sudo ansible-playbook -i hosts tambahan1.yml -k
    ```

    

    ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\52.png)

    

  * Setelah berhasil menjalankan ansible playbook hosts tambahan1.yml, maka step terakhir yaitu mengakses url vm.local/blog

    

    ![](C:\Users\TRIA YULITA\Downloads\PRAK MODUL 2\53.png)

    

    

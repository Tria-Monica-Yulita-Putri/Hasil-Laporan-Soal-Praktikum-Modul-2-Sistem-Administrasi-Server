*HASIL LAPORAN SOAL PRAKTIKUM MODUL 2 SISTEM ADMINISTRASI SERVER**

1. Pertama-tama rubah LXC landing dengan ubuntu focal (destroy n create, same ip, same name)

   ```markdown
   lxc-ls -f
   ```

   ```markdown
   rm /var/lib/lxc/ubuntu_landing/lxc_snapshots
   lxc-destroy ubuntu_landing
   ```

   

   ![1](https://user-images.githubusercontent.com/92940432/144348962-a32ed6e1-412a-4703-8085-11099617489e.png)

   

   * Lalu, langkah selanjutnya yaitu create ubuntu_landing

     ```markdown
     sudo lxc-create -n ubuntu_landing -t download -- --dist ubuntu --release focal --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
     ```

     

     ![2](https://user-images.githubusercontent.com/92940432/144348968-28b930f1-b727-4d3f-90f8-7ba7d3181be9.png)

     

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

     

     ![3](https://user-images.githubusercontent.com/92940432/144348970-c4079ee8-5348-4ce9-9c46-5a7c5f424801.png)

     

   * Setelah instal nano net-tools berhasil, maka langkah selanjutnya yaitu atur IP

     ```markdown
     nano /etc/netplan/10-lxc.yaml
     ```

     

     ![4](https://user-images.githubusercontent.com/92940432/144348971-71eed8d1-7f4b-4d92-9d80-00ad4bce73cf.png)

     

   * Setelah mengatur IP, maka langkah selanjutnya yaitu mengganti IP

     ```markdown
     netplan apply
     ```

     ```markdown
     ip r
     ```

     

     ![5](https://user-images.githubusercontent.com/92940432/144349433-1e5d94ee-d910-436a-91ee-b78d658d2e2d.png)

     

   * Setelah IP berhasil diganti, maka langkah selanjutnya yaitu instal ssh pada server

     ```markdown
     apt install openssh-server python -y
     ```

     

     ![6](https://user-images.githubusercontent.com/92940432/144348975-a8061340-2876-4cfb-8146-03e6a8b8176f.png)

     

   * Setelah berhasil install ssh, maka langkah berikutnya yaitu masuk sshd_config untuk mengatur permit login 

     ```markdown
     nano sshd_config
     ```

     

     ![7](https://user-images.githubusercontent.com/92940432/144348976-6acc16c5-0181-41a9-933e-9b90afda47b8.png)

     

   * Setelah mengatur permit login di sshd_config, maka langkah selanjutnya yaitu setting password ssh 

     ``` markdown
     passwd
     ```

     ```markdown
     exit
     ```

     

     ![8](https://user-images.githubusercontent.com/92940432/144348978-6aae2f2a-4543-42a0-839a-ed2ac6b992d9.png)

     

   * Setelah mengubah dan mengatur permit login di sshd_config dan berhasil setting password ssh, maka langkah selanjutnya yaitu mencoba masuk di ssh yang baru dan dapat dilihat bahwa bisa login dengan host yang baru yaitu 10.0.3.103

     ```markdown
     ssh root@10.0.3.103
     ```

     

     ![9](https://user-images.githubusercontent.com/92940432/144348981-6054c55d-49d1-41df-b149-d881ff80a79f.png)

     

     

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

   

   ![10](https://user-images.githubusercontent.com/92940432/144348983-8c0616c4-5df0-42f1-ba47-33336d0ba7b7.png)

   

   * Lalu, langkah selanjutnya yaitu membuat dan mendownload ubuntu_php7.4

     ```markdown
     sudo lxc-create -n ubuntu_php7.4 -t download -- --dist ubuntu --release focal --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
     ```

     

     ![11](https://user-images.githubusercontent.com/92940432/144348986-26e74343-eb8c-4ae9-bdb5-e3a6aff15547.png)

     

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

     

     ![12](https://user-images.githubusercontent.com/92940432/144348988-74e80a7f-59ac-4e09-a954-acf55f888a86.png)

     

   * Setelah install net-tools berhasil, maka step selanjutnya yaitu merubah IP Address ubuntu_php7.4 

     ```markdown
     nano /etc/netplan/10-lxc.yaml
     ```

     

     ![13](https://user-images.githubusercontent.com/92940432/144348990-85120352-a83c-4d41-883f-a02efbdca07b.png)

     

   * Setelah berhasil merubah IP Address ubuntu_php7.4, lalu step selanjutnya yaitu mengapply IP ubuntuphp7 lalu coba menampilkan IP root nya

     ```markdown
     root@ubuntuphp7:~# netplan apply
     ```

     ```markdown
     ip r
     ```

     

     ![14](https://user-images.githubusercontent.com/92940432/144348991-a64bace9-6481-41b6-bfc8-6a39ae88063d.png)

     

   * Setelah berhasil merubah dan ditampilkan IP root nya, maka langkah selanjutnya yaitu install openssh server

     ```markdown
     apt install openssh-server python -y
     ```

     

     ![15](https://user-images.githubusercontent.com/92940432/144348994-c2ca7702-51a2-4c4b-b692-cf01bee7b6f2.png)

     

   * Setelah berhasil menginstall openssh server, maka langkah selanjutnya yaitu mengedit sshd_config 

     ```markdown
     cd /etc/ssh
     ```

     ```markdown
     nano sshd_config
     ```

     

     ![16](https://user-images.githubusercontent.com/92940432/144349705-8d25a562-cd8b-4e7d-8c99-ecd3ba4ec66b.png)

     

   * Setelah berhasil mengedit sshd_config, lalu langkah selanjutnya yaitu restart ssh dan type the new password 

     ```markdown
     service sshd restart
     ```

     ```markdown
     passwd
     exit
     ```

     

     ![17](https://user-images.githubusercontent.com/92940432/144349711-3d150582-69cf-4ab8-be3c-9174473e2e23.png)

     

   * Setelah berhasil restart sshd dan type the new password, maka step selanjutnya yaitu mencoba connect ke ssh 10.0.3.101

     ```markdown
     ssh root@10.0.3.101
     ```

     

     ![18](https://user-images.githubusercontent.com/92940432/144349712-ad996a6a-eb21-48a3-8105-59b17d0e8efb.png)

     

3. vm.local/

   * Pertama-tama yaitu membuat directory laravel 8 pada lxc_landing

     ```markdown
     mkdir laravel
     ```

     ```markdown
     cd laravel/
     ```

     
     
     ![19](https://user-images.githubusercontent.com/92940432/144349722-c1794187-da2a-4936-8164-4690b38e95fb.png)


     

   * Setelah membuat directory laravel 8, maka langkah selanjutnya yaitu mengatur konfigurasi ansible di nano hosts dan nano nginxphp.yml

     ```markdown
     nano hosts
     ```

     ```markdown
     [landing]
     ubuntu_landing ansible_host=lxc_landing.dev ansible_ssh_user=root ansible_become_pass=1234
     ```
     
     
     
     ![20](https://user-images.githubusercontent.com/92940432/144349726-1a827524-1ad5-4447-8bb4-e0357b333a99.png)
     
     
     
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
     
     
     
     ![21](https://user-images.githubusercontent.com/92940432/144349729-b7939409-b9be-4850-9362-648b3b16efea.png)
     
     

   * Setelah berhasil di konfigurasi, maka langkah selanjutnya yaitu mencoba untuk menjalankan ansible playbook nginxphp.yml

     ```markdown
     ansible-playbook -i hosts nginxphp.yml -k
     ```

     

     ![22](https://user-images.githubusercontent.com/92940432/144349734-b3b71b1c-b423-4f90-9643-bff303983dac.png)

     

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

     

     ![23](https://user-images.githubusercontent.com/92940432/144349742-470fe6a8-29dc-4290-9c86-8ba978f2505e.png)

     

   * Setelah membuat file install composer.yml, maka langkah selanjutnya yaitu menjalankan ansible playbook installcomposer.yml

     ```markdown
     ansible-playbook -i hosts installcomposer.yml -k
     ```

     

     ![24](https://user-images.githubusercontent.com/92940432/144349745-2a87653b-f823-4964-9e6c-4ac28ce7e18c.png)

     

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

     

     ![25](https://user-images.githubusercontent.com/92940432/144349753-40998fbf-42c1-4b4b-823b-1d33a91c2c3a.png)

     

   * Setelah setting lxc_landing dilakukan, maka step selanjutnya yaitu setting config.yml

     ```markdown
     nano config.yml
     ```

     ```
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

     

     ![26](https://user-images.githubusercontent.com/92940432/144349755-35517f27-fa04-466e-97a2-3d3063a56f85.png)


     

   * Setelah setting config.yml, maka langkah selanajutnya yaitu coba memanggil config.yml

     ```markdown
      ansible-playbook -i hosts config.yml -k
     ```

     

     ![27](https://user-images.githubusercontent.com/92940432/144349758-e36e0b84-c07f-44a8-90f7-b5da8afa3dee.png)

     

   * Setelah berhasil dijalankan, maka langkah step selanjutnya yaitu mengakses url vm.local

     

     ![28](https://user-images.githubusercontent.com/92940432/144349765-2cfc4d67-9530-448f-823f-33bd062a88b0.png)

     

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

     

     ![29](https://user-images.githubusercontent.com/92940432/144349775-21310b25-4481-42c1-8dff-03ce932dc6e8.png)

     

   * Setelah berhasil install, maka langkah selanjutnya yaitu masuk dan setting wordpress nano host 
   
     ```markdown
     nano hosts
     ```

     

     ![30](https://user-images.githubusercontent.com/92940432/144349779-cf62ceb9-a6bf-470e-9b3e-4e7cbad356f0.png)

     

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
   
     
   
     
   
     ![31](https://user-images.githubusercontent.com/92940432/144350154-3f3dd777-ab05-4862-b019-84d652273d3f.png)
   
     
   
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
   
     
   
     
   
     ![33](https://user-images.githubusercontent.com/92940432/144350157-88170491-2d0a-42d0-b545-ef7f83b42891.png)
   
     
   
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
   
     
   
     
   
     ![34](https://user-images.githubusercontent.com/92940432/144350160-78857d42-fbc6-4e5a-939b-2dc4a4e6f7a6.png)
   
     
   
   * Setelah setting di nano wordpress.conf, maka step selanjutnya yaitu mencoba memanggil hosts installwordpress.yml 
   
     ```markdown
     sudo ansible-playbook -i hosts installwordpress.yml -k
     ```
   
     
   
     ![35](https://user-images.githubusercontent.com/92940432/144350163-c97314e1-a5db-49c4-8acf-e765023c87b6.png)
   
     
   
   * Setelah ansible playbook installwordpress.yml berhasil dijalankan, maka step terakhir yaitu akses url vm.local/blog 
   
     
   
     ![36](https://user-images.githubusercontent.com/92940432/144350175-31fae38a-61b2-45b8-8255-e4eb0862efe9.png)

   
     
   
     * Coba sign in atau membuat akun wordpress yang berisi title (judul), username dan juga password
   
       
   
       ![37](https://user-images.githubusercontent.com/92940432/144350177-b6bc86a5-4556-4564-b3a2-881799730ccb.png)
   
     
   
     * Setelah membuat akun, maka tampilan akan seperti gambar dibawah ini, yang berarti sudah sukses membuat akun wordpress dengan username admin
   
       
   
       ![38](https://user-images.githubusercontent.com/92940432/144350348-ac0deeb2-ffc6-4719-a67c-13de0a476412.png)
   
     
   
     * Setelah itu kita coba login wordpress dengan username dan password yang sudah dibuat tadi
   
       
       
       ![39](https://user-images.githubusercontent.com/92940432/144350188-fdddf16e-87fa-4f3a-8ba8-593a40af76d1.png)
   
     
   
     * Setelah login, maka akan terdapat tampilan dashboard wordpress seperti gambar dibawah ini
   
       
   
       ![40](https://user-images.githubusercontent.com/92940432/144350194-abad3eb4-8bf3-49b4-869c-cff382b14096.png)
   
     
   
     * Setelah berhasil masuk ke dashboard wordpress, maka coba refresh vm.local/blog, dan akan muncul tampilan seperti gambar dibawah ini
   
       
   
       ![41](https://user-images.githubusercontent.com/92940432/144350201-233bdfa7-23c8-43fe-9c1a-4fcd79d99557.png)

     
     


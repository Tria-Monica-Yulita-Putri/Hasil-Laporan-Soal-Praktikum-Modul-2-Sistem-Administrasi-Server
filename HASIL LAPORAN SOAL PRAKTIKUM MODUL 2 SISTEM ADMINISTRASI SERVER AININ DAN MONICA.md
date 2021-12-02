# **HASIL LAPORAN SOAL PRAKTIKUM MODUL 2 SISTEM ADMINISTRASI SERVER**

1. Pertama-tama rubah LXC landing dengan ubuntu focal (destroy n create, same ip, same name)

   ```markdown
   lxc-ls -f
   ```

   ```markdown
   rm /var/lib/lxc/ubuntu_landing/lxc_snapshots
   lxc-destroy ubuntu_landing
   ```

   

   ![1](https://user-images.githubusercontent.com/92940432/144391352-7bdcfab1-05fd-4f79-8118-40459561c2eb.png)

   

   * Lalu, langkah selanjutnya yaitu create ubuntu_landing

     ```markdown
     sudo lxc-create -n ubuntu_landing -t download -- --dist ubuntu --release focal --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
     ```

     

     ![2](https://user-images.githubusercontent.com/92940432/144391379-a97cc80b-bd86-492e-8ee8-5cfaba433c1c.png)

     

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

     

     ![3](https://user-images.githubusercontent.com/92940432/144391382-1f385486-38af-4213-ab33-f2d636bc9453.png)

     

   * Setelah instal nano net-tools berhasil, maka langkah selanjutnya yaitu atur IP

     ```markdown
     nano /etc/netplan/10-lxc.yaml
     ```

     

     ![4](https://user-images.githubusercontent.com/92940432/144391391-daa63206-c1e9-47c3-8069-717d1a83744f.png)

     

   * Setelah mengatur IP, maka langkah selanjutnya yaitu mengganti IP

     ```markdown
     netplan apply
     ```

     ```markdown
     ip r
     ```

     

     ![5](https://user-images.githubusercontent.com/92940432/144391394-1f75bb86-e02e-4e10-abda-01a30e4a68ed.png)

     

   * Setelah IP berhasil diganti, maka langkah selanjutnya yaitu instal ssh pada server

     ```markdown
     apt install openssh-server python -y
     ```

     

     ![6](https://user-images.githubusercontent.com/92940432/144391401-7a865914-7fd2-4e1e-be91-dc6536971d67.png)

     

   * Setelah berhasil install ssh, maka langkah berikutnya yaitu masuk sshd_config untuk mengatur permit login 

     ```markdown
     nano sshd_config
     ```

     

     ![7](https://user-images.githubusercontent.com/92940432/144391407-c7203048-f670-4078-914c-752565ab6ec1.png)

     

   * Setelah mengatur permit login di sshd_config, maka langkah selanjutnya yaitu setting password ssh 

     ``` markdown
     passwd
     ```

     ```markdown
     exit
     ```

     

     ![8](https://user-images.githubusercontent.com/92940432/144391409-e1b78740-207b-47b0-b9c2-9d23eec04c5b.png)

     

   * Setelah mengubah dan mengatur permit login di sshd_config dan berhasil setting password ssh, maka langkah selanjutnya yaitu mencoba masuk di ssh yang baru dan dapat dilihat bahwa bisa login dengan host yang baru yaitu 10.0.3.103

     ```markdown
     ssh root@10.0.3.103
     ```

     

     ![9](https://user-images.githubusercontent.com/92940432/144391413-c79ba3a8-8a02-4217-8be6-7d63b063e1dd.png)

     

     

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

   

   ![10](https://user-images.githubusercontent.com/92940432/144391425-6023e979-8844-412e-ba05-be077345bb40.png)

   

   * Lalu, langkah selanjutnya yaitu membuat dan mendownload ubuntu_php7.4

     ```markdown
     sudo lxc-create -n ubuntu_php7.4 -t download -- --dist ubuntu --release focal --arch amd64 --force-cache --no-validate --server images.linuxcontainers.org
     ```

     

     ![11](https://user-images.githubusercontent.com/92940432/144391442-65e55d03-5d16-4711-aab2-82c9df255d4d.png)

     

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

     

     ![12](https://user-images.githubusercontent.com/92940432/144391446-57a692ff-9bf1-4dc6-8a8c-5b7fd31eed3a.png)

     

   * Setelah install net-tools berhasil, maka step selanjutnya yaitu merubah IP Address ubuntu_php7.4 

     ```markdown
     nano /etc/netplan/10-lxc.yaml
     ```

     

     ![13](https://user-images.githubusercontent.com/92940432/144391454-5e7278da-c349-4de3-bca4-7eeb6497d06d.png)


     

   * Setelah berhasil merubah IP Address ubuntu_php7.4, lalu step selanjutnya yaitu mengapply IP ubuntuphp7 lalu coba menampilkan IP root nya

     ```markdown
     netplan apply
     ```

     ```markdown
     ip r
     ```

     

     ![14](https://user-images.githubusercontent.com/92940432/144391461-13b60404-ef8c-4704-9704-d884948dd4a4.png)

     

   * Setelah berhasil merubah dan ditampilkan IP root nya, maka langkah selanjutnya yaitu install openssh server

     ```markdown
     apt install openssh-server python -y
     ```

     

     ![15](https://user-images.githubusercontent.com/92940432/144391464-c11bf104-8573-4453-90f6-c2213c623926.png)

     

   * Setelah berhasil menginstall openssh server, maka langkah selanjutnya yaitu mengedit sshd_config 

     ```markdown
     cd /etc/ssh
     ```

     ```markdown
     nano sshd_config
     ```

     

     ![16](https://user-images.githubusercontent.com/92940432/144391925-163baeda-ec36-47ef-a299-a94f802abced.png)

     

   * Setelah berhasil mengedit sshd_config, lalu langkah selanjutnya yaitu restart ssh dan type the new password 

     ```markdown
     service sshd restart
     ```

     ```markdown
     passwd
     exit
     ```

     

     ![17](https://user-images.githubusercontent.com/92940432/144391937-65549b00-180a-46ef-8d46-6beacae54505.png)

     

   * Setelah berhasil restart sshd dan type the new password, maka step selanjutnya yaitu mencoba connect ke ssh 10.0.3.101

     ```markdown
     ssh root@10.0.3.101
     ```

     

     ![18](https://user-images.githubusercontent.com/92940432/144391942-d183cc64-01fa-470b-a018-d206a37b2051.png)

     

3. vm.local/

   * Pertama-tama yaitu membuat directory laravel 8 pada lxc_landing

     ```markdown
     mkdir laravel
     ```

     ```markdown
     cd laravel/
     ```

     
     
     ![19](https://user-images.githubusercontent.com/92940432/144391957-9c50fa0b-1ce1-4658-bb4a-174751b6d11d.png)

     

   * Setelah membuat directory laravel 8, maka langkah selanjutnya yaitu mengatur konfigurasi ansible di nano hosts dan nano nginxphp.yml

     ```markdown
     nano hosts
     ```

     ```markdown
     [landing]
     ubuntu_landing ansible_host=lxc_landing.dev ansible_ssh_user=root ansible_become_pass=1234
     ```
     
     
     
     ![20](https://user-images.githubusercontent.com/92940432/144391962-00b5fd3e-91c3-408d-b832-bee56ec6eef5.png)
     
     
     
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
     
     
     
     ![21](https://user-images.githubusercontent.com/92940432/144391964-8dac0f1d-970a-4fa5-ac64-3f0b014d14c5.png)
     
     

   * Setelah berhasil di konfigurasi, maka langkah selanjutnya yaitu mencoba untuk menjalankan ansible playbook nginxphp.yml

     ```markdown
     ansible-playbook -i hosts nginxphp.yml -k
     ```

     

     ![22](https://user-images.githubusercontent.com/92940432/144391970-4de5b33b-e361-454b-906c-a16360503da9.png)

     

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

     

     ![23](https://user-images.githubusercontent.com/92940432/144391986-3e258763-727d-43c1-b9f0-5b1f6b668d17.png)


     

   * Setelah membuat file install composer.yml, maka langkah selanjutnya yaitu menjalankan ansible playbook installcomposer.yml

     ```markdown
     ansible-playbook -i hosts installcomposer.yml -k
     ```

     

     ![24](https://user-images.githubusercontent.com/92940432/144391992-508b1e49-924c-4b8a-bee5-5d9529f410a5.png)


     

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

     

     ![25](https://user-images.githubusercontent.com/92940432/144392005-0adad875-ebdf-453b-a6de-8c1b7ba1923b.png)

     

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

     

     ![26](https://user-images.githubusercontent.com/92940432/144392010-492b573c-dbe4-4c07-a818-f2d7f9348520.png)
     

   * Setelah setting config.yml, maka langkah selanajutnya yaitu coba memanggil config.yml

     ```markdown
      ansible-playbook -i hosts config.yml -k
     ```

     

     ![27](https://user-images.githubusercontent.com/92940432/144392017-e89d75e5-8a16-4e37-ad9d-0a014cc9da58.png)


     

   * Setelah berhasil dijalankan, maka langkah step selanjutnya yaitu mengakses url vm.local

     

     ![28](https://user-images.githubusercontent.com/92940432/144392025-bdc5be0e-7947-4122-90aa-0974a21d842a.png)


     

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

     

     ![29](https://user-images.githubusercontent.com/92940432/144392034-e13534eb-6c04-4162-b827-4ba35c86fadf.png)

     

   * Setelah berhasil install, maka langkah selanjutnya yaitu masuk dan setting wordpress nano host 
   
     ```markdown
     nano hosts
     ```

     

     ![30](https://user-images.githubusercontent.com/92940432/144392038-3110cc4a-b2ef-4f60-b6de-23f95b4de150.png)

     

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
   
     
   
     
   
     ![31](https://user-images.githubusercontent.com/92940432/144392042-08d38383-584e-487b-aa27-03ca891ff650.png)
   
     
   
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
   
     
   
     
   
     ![33](https://user-images.githubusercontent.com/92940432/144392045-0b43de3a-5dc7-460d-95f8-46a30fe0dfc8.png)
   
     
   
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
   
     
   
     
   
     ![34](https://user-images.githubusercontent.com/92940432/144392051-affc6cca-7252-4442-829b-3c5661ae03bc.png)
   
     
   
   * Setelah setting di nano wordpress.conf, maka step selanjutnya yaitu mencoba memanggil hosts installwordpress.yml 
   
     ```markdown
     sudo ansible-playbook -i hosts installwordpress.yml -k
     ```
   
     
   
     ![35](https://user-images.githubusercontent.com/92940432/144392055-4a5f4c8a-6e9c-4f0c-87d0-8f4cd7b6aed1.png)
   
     
   
   * Setelah ansible playbook installwordpress.yml berhasil dijalankan, maka step terakhir yaitu akses url vm.local/blog 
   
     
   
    ![36](https://user-images.githubusercontent.com/92940432/144392061-cd5ecaf0-ebb7-446a-9623-0e32b520bb6d.png)
   
     
   
     * Coba sign in atau membuat akun wordpress yang berisi title (judul), username dan juga password
   
       
   
       ![37](https://user-images.githubusercontent.com/92940432/144392064-2265aaec-fcaa-4344-af63-dd19fe4de6cb.png)
   
     
   
     * Setelah membuat akun, maka tampilan akan seperti gambar dibawah ini, yang berarti sudah sukses membuat akun wordpress dengan username admin
   
       
   
       ![38](https://user-images.githubusercontent.com/92940432/144392067-cd2d6ba9-a093-4919-9ef1-772f0101ca32.png)
   
     
   
     * Setelah itu kita coba login wordpress dengan username dan password yang sudah dibuat tadi
   
       
       
       ![39](https://user-images.githubusercontent.com/92940432/144392071-701a0591-ba79-48ab-a422-7449d762a411.png)
   
     
   
     * Setelah login, maka akan terdapat tampilan dashboard wordpress seperti gambar dibawah ini
   
       
   
       ![40](https://user-images.githubusercontent.com/92940432/144392073-9ae3d309-1fb3-49b6-b88b-775395d7653f.png)
   
     
   
     * Setelah berhasil masuk ke dashboard wordpress, maka coba refresh vm.local/blog, dan akan muncul tampilan seperti gambar dibawah ini
   
       
   
       ![41](https://user-images.githubusercontent.com/92940432/144392795-28a3571d-8f9d-4c46-ace0-9f1fc52afb45.png)
     



## **SOAL TAMBAHAN**

- Rubah konfigurasi php7.4 yang semula menggunakan socket menjadi menggunakan port (127.0.0.1:9001) 

  #### **Untuk vm.local (laravel)**

  * Pertama-tama masuk ke nano lxc_landing.dev untuk mengubah konfigurasi di dalam nano lxc_landing.dev dengan port 127.0.0.1:9001

    ```markdown
    nano lxc_landing.dev
    ```

    

    ![42](https://user-images.githubusercontent.com/92940432/144392823-a1e3a0b4-8411-4441-90b4-eb61b70b1f0a.png)

    

    ![43](https://user-images.githubusercontent.com/92940432/144392829-a721da78-69ec-4949-841b-4bc6a1b69573.png)

    

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

    

    

    ![44](https://user-images.githubusercontent.com/92940432/144392836-53435977-82c0-48f4-a4f8-d6a07d4a2212.png)


    

    ![45](https://user-images.githubusercontent.com/92940432/144392840-0ff2604e-c97a-4568-8ec4-da0bb5cc16f3.png)

    

  * Setelah berhasil diganti, maka langkah selanjutnya yaitu mencoba menjalankan ansible playbook hosts tambahan1.yml

    ```markdown
    ansible-playbook -i hosts tambahan1.yml -k
    ```

    

    ![46](https://user-images.githubusercontent.com/92940432/144392851-782cf283-19f4-4617-81e4-a70dba391b06.png)

    

  * Setelah berhasil menjalankan ansible playbook hosts tambahan1.yml, maka langkah selanjutnya yaitu mengakses url vm.local

    

    ![47](https://user-images.githubusercontent.com/92940432/144392860-aa7d6549-694a-4735-a17a-4bab97cd4f16.png)


    

  #### **Untuk vm.local/blog (wordpress)**

  * Pertama-tama masuk ke nano wordpress.conf untuk mengubah konfigurasi di dalam nano wordpress.conf  dengan port 127.0.0.1:9001

    ```markdown
    nano wordpress.conf
    ```

    

    ![48](https://user-images.githubusercontent.com/92940432/144392867-8cb89aba-786b-478d-b2ec-242f064520a8.png)

    

    ![49](https://user-images.githubusercontent.com/92940432/144392873-d6c750ca-5f67-4186-86b4-fc3146ab6277.png)

    

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

    

    

    ![50](https://user-images.githubusercontent.com/92940432/144392878-8dfb2c51-607f-402e-bfab-6826bd73d494.png)

    

    ![51](https://user-images.githubusercontent.com/92940432/144392884-014afce6-b4d7-46bd-a548-10b002ba2e83.png)

    

  * Setelah berhasil diganti, maka langkah selanjutnya yaitu mencoba menjalankan ansible playbook hosts tambahan1.yml

    ```markdown
    sudo ansible-playbook -i hosts tambahan1.yml -k
    ```

    

    ![52](https://user-images.githubusercontent.com/92940432/144392891-7502d589-3b9f-4269-8f19-18071f79ff8d.png)

    

  * Setelah berhasil menjalankan ansible playbook hosts tambahan1.yml, maka step terakhir yaitu mengakses url vm.local/blog

    

    ![53](https://user-images.githubusercontent.com/92940432/144392909-bcaca22d-eaa9-4966-a6fd-1b7d04ecc2e9.png)

    

    

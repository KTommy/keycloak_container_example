FROM httpd:2.4

RUN echo "now building httpd ..."

#############################################

# when using your own httpd.conf, uncomment below
# COPY ./my-httpd.conf /usr/local/apache2/conf/httpd.conf

# configuration of mod_auth_openidc
COPY ./my_auth_openidc.conf /usr/local/apache2/conf/my_auth_openidc.conf

# set self certification
COPY ./server.crt /usr/local/apache2/conf/
COPY ./server.key /usr/local/apache2/conf/

RUN sed -i \
        -e 's/^#\(Include .*httpd-ssl.conf\)/\1/' \
        -e 's/^#\(LoadModule .*mod_ssl.so\)/\1/' \
        -e 's/^#\(LoadModule .*mod_socache_shmcb.so\)/\1/' \
        conf/httpd.conf

RUN apt update

# enable when you want to use them for debugging etc.
# RUN sh -c "echo y | apt install iputils-ping"
# RUN sh -c "echo y | apt install net-tools"
# RUN sh -c "echo y | apt install netcat"
# RUN sh -c "echo y | apt install curl"
# RUN sh -c "echo y | apt install vim"

RUN sh -c "echo y | apt install libapache2-mod-auth-openidc"

RUN echo "" >> conf/httpd.conf
RUN echo "LoadModule auth_openidc_module modules/mod_auth_openidc.so" >> conf/httpd.conf
RUN echo "Include conf/auth_openidc.conf" >> conf/httpd.conf

RUN ln /usr/lib/apache2/modules/mod_auth_openidc.so modules/
RUN ln /etc/apache2/mods-available/auth_openidc.conf conf/
RUN cat conf/my_auth_openidc.conf >> conf/auth_openidc.conf

#############################################
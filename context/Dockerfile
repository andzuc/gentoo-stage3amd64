# name the portage image
FROM andzuc/gentoo-portage:latest as portage

# image is based on stage3-amd64
FROM andzuc/gentoo-stage3:latest

# copy the entire portage volume in
COPY --from=portage /var/db/repos/gentoo /var/db/repos/gentoo

RUN emerge --sync \
    && FEATURES="-sandbox -usersandbox -ipc-sandbox -mount-sandbox -network-sandbox -pid-sandbox" emerge -vuDN @world \
    && emerge --depclean \
    && emerge --info \
    && (cd /var/db/pkg/ && ls -d */*)

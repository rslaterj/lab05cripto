# lab05cyser
## Paso 2
```
sed -i 's/OpenSSH_8.3/OpenSSH_?/g' version.h .pc/package-versioning.patch/version.h debian/patches/package-versioning.patch ; \
sed -i 's/SSH_VERSION SSH_PORTABLE/SSH_VERSION/' version.h .pc/package-versioning.patch/version.h debian/patches/package-versioning.patch ; \
sed -i 's/ " " SSH_EXTRAVERSION//' version.h debian/patches/package-versioning.patch
```
```
autoreconf -i && ./configure && make && make install
```

## Paso 3
```
echo "KexAlgorithms=curve25519-sha256" | tee -a /etc/ssh/sshd_config
echo "Ciphers=aes128-ctr" | tee -a /etc/ssh/sshd_config
echo "MACs=hmac-sha2-256" | tee -a /etc/ssh/sshd_config
echo "Compression=no" | tee -a /etc/ssh/sshd_config
```
```
service ssh restart
```

```
docker start c4
```

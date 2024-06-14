https://metacpan.org/dist/perl-ldap/view/lib/Net/LDAP.pod#start_tls
https://metacpan.org/pod/Net::LDAP
https://metacpan.org/pod/Net::LDAPS
https://support.ssl.com/Knowledgebase/Article/View/19/0/der-vs-crt-vs-cer-vs-pem-certificates-and-how-to-convert-them

When verifying the server's certificate, either set capath to the pathname of the directory containing
CA certificates, or set cafile to the filename containing the certificate of the CA who signed the
server's certificate. These certificates must all be in PEM format.

The directory in 'capath' must contain certificates named using the hash value of the certificates' subject names.
To generate these names, use OpenSSL & ln like below in Unix.

In Git Bash:

cd /D/EdaTk/ldap_auth_perl/certificates

openssl x509 -in Siemens_OneAD_Root_CA_exp2026-09-10.cer     -outform pem -out Siemens_OneAD_Root_CA_exp2026-09-10.pem
openssl x509 -in Siemens_PLM-Root_CA_exp2038-06-26.cer       -outform pem -out Siemens_PLM-Root_CA_exp2038-06-26.pem
openssl x509 -in Siemens_Root_CA_V3.0_2016_exp2028-06-06.cer -outform pem -out Siemens_Root_CA_V3.0_2016_exp2028-06-06.pem

ln -s Siemens_OneAD_Root_CA_exp2026-09-10.pem     `openssl x509 -hash -noout < Siemens_OneAD_Root_CA_exp2026-09-10.pem`.0
ln -s Siemens_PLM-Root_CA_exp2038-06-26.pem       `openssl x509 -hash -noout < Siemens_PLM-Root_CA_exp2038-06-26.pem`.0
ln -s Siemens_Root_CA_V3.0_2016_exp2028-06-06.pem `openssl x509 -hash -noout < Siemens_Root_CA_V3.0_2016_exp2028-06-06.pem`.0

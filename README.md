# TIPS_DOD 

# Sacar subdomain con "curl" 

    curl -s "https://crt.sh/?q=.mil" | grep .mil | tr 'B' '\n' | tr 'R>\/<TD\/' ' ' | xargs -I @ echo @ | sort -u | anew | tee sub_.mil.txt

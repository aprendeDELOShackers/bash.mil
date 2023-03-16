# TIPS_DOD 

# Sacar subdomain con "curl" 

    curl -s "https://crt.sh/?q=.mil" | grep .mil | tr 'B' '\n' | tr 'R>\/<TD\/' ' ' | xargs -I @ echo @ | sort -u | anew | tee sub_.mil.txt


# extraer_URL
    
    #!/usr/bin/bash

    #Extrae todas la url de un sitios web y filtarar  loa mas intresante
    domain=$1

    extraer_URL(){
        mkdir -p $domain $domain/URL  $domain/fileJS $domain/gf
        echo $domain | waybackurls | tee $domain/URL/wayback1.txt
        cat $domain/URL/wayback1.txt | uro | egrep -iv ".(jpg|jpeg|png|svg|git|woff|woff2|pdf|ico|tif|tif.f|css|jsp|jsp|txt|html|htm)" | tee $domain/URL/url_filtre.txt
        rm $domain/URL/wayback1.txt 2> /dev/null

    }
    extraer_URL

    ####################################################################################

    file_js(){
        cat $domain/URL/url_filtre.txt | grep -E "\.js(?:onp?)?$" | anew $domain/fileJS/js.txt
        cat $domaind/fileJS/js.txt | hakcheckurl | grep -v 404 | anew $domain/fileJS/200js.txt

    }
    file_js]}

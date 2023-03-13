
⚠️NOTE: Hello friends, this bot is made for educational purposes 
❗ those who use this bot are not entirely my responsibility,
 it is your responsibility, your responsibility is entirely your responsibility.

#içe aktarma  istekleri
ithalat  zamanı
 csv'yi içe aktar

# API anahtarınızı buradan alın: https://scraptik.com

scraptik_apikey  =  "API ANAHTARI BURAYA GİRİN"

#Bakmak istiyorsan Hizmetler altında Scraptik "Kimlik için Kullanıcı Adı"nı kullan
user_id  =  "KULLANICI KİMLİĞİNİ BURAYA GİRİN"

alan adları  = [
    'benzersiz_kimlik' ,
    'uid' ,
    'bölge' ,
    'dil '
    "takip edilen_sayı" ,
    "takipçi_sayı" ,
    "favoriting_count" ,
    "ins_id" ,
    "youtube_channel_id" ,
    "youtube_channel_title" ,
    "twitter_id" ,
    "twitter_adı"
]

 f olarak açık ( r'data.csv' , 'w' , encoding = "utf-8" ) ile : 
    yazar  =  csv . yazar ( f )
    sıra  = {}
     alan adlarında x  için : 
        sıra [ x ] =  x
    yazar  =  csv . DictWriter ( f , alan adları = alan adları )
    yazar _ satır yazmak ( satır )
        
def  get_followers ( user_id , max_time ):
    deneyin :
        url  =  "https://scraptik.p.rapidapi.com/list-followers"
        
        sorgu dizesi  = {
            "kullanıcı_kimliği" : str ( kullanıcı_kimliği ),
            "sayım" : "100" ,
            "maks_zaman" : str ( maks_zaman )
        }

        başlıklar  = {
            'x-rapidapi-key' : scraptik_apikey ,
            'x-rapidapi-host' : "scraptik.p.rapidapi.com"
        }

        r  =  istekler . get ( url , başlıklar = başlıklar , parametreler = sorgu dizesi ). json ()

         r [ "takipçiler" ] içinde u  için : 
             f olarak açık ( r'data.csv' , 'a' , kodlama = "utf-8" ) ile : 
                yazar  =  csv . yazar ( f )
                sıra  = {}
                 alan adlarında x  için : 
                     u ve u [ x ] içinde x  ise :   
                        sıra [ x ] =  str ( u [ x ])
                        
                        if  x  ==  "uid" :
                            sıra [ x ] =  str ( u [ x ]) +  ''

                yazar  =  csv . DictWriter ( f , alan adları = alan adları , sınırlayıcı = ',' , quotechar = '"' , alıntı = csv . QUOTE_MINIMAL )
                yazar _ satır yazmak ( satır )

        eğer  r [ "has_more" ] ise:
            get_followers ( user_id , r [ "min_time" ])

     e olarak İstisna  dışında : 
        yazdır ( "Hata!" )
        yazdır ( repr ( e ))
        # yeniden dene?
        # get_followers(user_id, max_time)
    
get_followers ( user_id , int ( zaman .zaman ()) )

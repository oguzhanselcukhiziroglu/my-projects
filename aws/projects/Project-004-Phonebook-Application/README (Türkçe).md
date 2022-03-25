# Görevimiz bir telefon defteri dizayn etmek
# Clarusway reposundan gerekli dosyaları (.py ve .html uzantılı dosyalar ve template dosyası) çekeceğiz.
# Bu dosyaları localimize çekip flask'i yazdıktan sonra kendi github repomuza push edeceğiz.
# Bir tane template oluşturacağız. Bu template'de hem ordaki EC2 insatance'ların içine bir user data yazacağız
# Gerekli programları içine yükleyeceğiz (Flask, Python3, OS Update, Package Manager). Github repomuzdan gerekli dosyaları çekeceğiz.
# Bu örnekte private repo ile çalışacağız. (Private repodan nasıl dosya çekiliyor. Ona değineceğiz.)
# Sonra template'mizin, CloudFormation sonucu oluşacak stack bize RDS oluşturacak, RDS'in 'Security Grub'unu oluşturacak. 'Load Balancer'
# oluşturacak ve 'Auto Scaling Group' oluşturacak. Telefon numaraları ve isimleri RDS'te tutulacak.
# Biz niye 'Load Balancer' ve 'Auto Scaling Group' oluşturacağız? Artık bunlar marketteki best practice'lar. Yani bir mimaride genelde
# 'Load Balancer' ve 'Auto Scaling Group' oluşturulur. Uygulamamızda trafiği ilk önce 'Load Balancer' karşılar. Load Balancer gelen
# yükü dağıtır. Bizim yaptığımız çalışma bir internet telefon defteri. Aynı anda on binlerce kişi kayıt yapmaya ve search yapmaya
# çalışırsa load balancer oluşan yükü EC2 Instance'lara dağıtacak. Olayı ileri boyuta taşımak için instance'ları manuel oluşturmayacağız.
# Bunun yerine load balancerın yükü dağıtacağı instanceların talimatlarını vereyim 'Auto Scaling Group' kendisi oluştursun. Bizim
# belirleyeceğimiz 'minimum capacity', 'maximum capacity' ve 'desired capacity' değerlerine göre 'Auto Scaling Group' instance'ları
# kendisi oluşturacak. Yani bir DevOps Engineer mantığıyla herşeyi otomatize edeceğiz.

GitHub repona git.

Repositories bölümüne git.

'New' butonuna basarak 'private-my-projets' isminde yeni bir private repository oluşturacağız. (README file ekle)

Oluşturduğun 'private-my-projets' repository'sinin 'code' bölümüne git. Repoyu clone edeceğiz.

Masaüstüne git ve git bash'i aç.

'git clone https://github.com/oguzhanselcukhiziroglu/private-my-projets.git' komutunu çalıştır.

(Bu satırdan 51'nci satıra kadar olan adımlar 'token' oluşturmak için. Varsa oluşturma)

Reponda avatar resminin olduğu alana tıkla.

Gelen menüde 'Settings'e tıkla.

Açılan pencerede 'Developer Settings'e tıkla.

Açılan pencerede 'Personal Access Tokens'a tıkla.

Açılan pencerede 'Generate New Token'a tıkla.

Açılan 'Confirm Access' penceresine GitHub şifreni gir.

Açılan pencerede 'Note' kısmına token'ı neden kullanacağının bilgisini gir.

Expiration = No expiration

Bütün başlıkları tikli tale getir. (check/uncheck)

'Generate token' butonuna tıkla.

Açılan pencerede 'ghp_7hvHOZQ3hUyG70swK7mr55yqhXF1tp1unDN7' benzeri çıkan token'ı kopyala ve kaybetmeyeceğin bir dosyada muhafaza et.

# Not: Token'ı 'user data'yı yazarken kullanacağız.

GitHub'ta repositories kısmına git ve son oluşturduğumuz 'private-my-projects' klasörüne gir.

Bu arada 'clarusway-aws-10-21' reponu güncelle. (Bende AWS_DevOps) # git pull upstream main --- git push origin

Masaüstünde yer alan 'AWS_DevOps/aws/projects/' dosya dizinine git ve 'Project-004-Phonebook-Application' klasörünü kopyala.

Biraz evvel klonladığın 'private-my-projects' klasörü içine 'Project-004-Phonebook-Application' klasörünü yapıştır.

'Project-004-Phonebook-Application' klasörünü VSCode ile çalıştır.

Açılan dosyalar incelendiğinde 'add-update.html', 'delete.html' ve 'index.html' gibi template dosyaları ile 'phonebook-app.py'
dosyasının hazır olduğunu göreceğiz. Bizden istenen bu mimariyi ayağa kaldıracak CloudFormation. Geri kalan kısmı
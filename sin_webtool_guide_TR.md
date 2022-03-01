# Özellikleri
    
-   Madeni para gönderim özelliği
-   Ekli bilgileri içeren fatura ödeme işlemi
-   E-Yönetişim oyu verebilme
-   Yeni özellikler çok yakında
    
# Bir KeyFile oluşturun
    

En son sürümü şuradan indirin: [https://github.com/SINOVATEblockchain/SINWebTool/releases/](https://github.com/SINOVATEblockchain/SINWebTool/releases/)

Dosyaları bilgisayarınızdaki uygun bir klasöre çıkarın.
 

![](assets/img/sin_webtool_guide/webtool01.png)


**WebToolOpenWithaBrowser** dosyasına çift tıklayınğınızda, geçerli tarayıcınızda SIN WebTool açılacaktır.

Online Modda kullanmak için SIN-core cüzdanınızı açın. Üzerinde işlem yapmak istediğiniz adresi Coin Control penceresinden bulup kopyalayın.
 

![](assets/img/sin_webtool_guide/webtool02.png)  
  

 Help/Debug Window menüsünü takip ederek Console sekmesine ulaşın.

Cüzdanınız şifreli ise aşağıdaki adımları uygulayarak geçici bir süre şifreyi devre dışı bırakın.



![](assets/img/sin_webtool_guide/webtool03.png)

  
**yourpassword:** bunun yerine geçerli cüzdan şifrenizi giriniz.

**1000:** Örnek olarak 1000 saniye süresince cüzdanın şifresi açılmıştır. Siz kendinize göre bir süre belirleyebilirsiniz.
 

**Not:** Cüzdanınız şifreli değilse bu aşamayı atlayabilirsiniz. Ancak cüzdanınızı bir şifre ile korumanızı şiddetle tavsiye ederiz.


Bu işlemlerden sonra Key File oluşturma aşamasına geçebiliriz.
  
  
![](assets/img/sin_webtool_guide/webtool04.png)


**youraddress:** Coin Control penceresinde kopyaladığımız ve üzerinde işlem yapacağımız adres.
**newpassphrase:** SIN WebTool üzerinde yapacağımız işlemler için gerekli olan yeni bir parola.


**Örnek:**


![](assets/img/sin_webtool_guide/webtool05.png)

  
Komutu çalıştırdığımızda bir key file üretilir. Key dosyasını SIN-qt dosyasını çalıştırdığınız klasörde bulabilirsiniz.


![](assets/img/sin_webtool_guide/webtool06.png)


![](assets/img/sin_webtool_guide/webtool07.png)

  
Tarayıcınızda SIN WebTool’u açın ve **Choose File** butonuna tıklayın. 


  
![](assets/img/sin_webtool_guide/webtool08.png)

  
  

Sizden keyfile dosyasını belirtmeniz istenecek. Keyfile dosyası SIN-qt ile aynı klasörde bulunduğundan bu klasöre ilerleyiniz. 


Keyfile dosyasını seçerek open butonuna tıklayınız.



![](assets/img/sin_webtool_guide/webtool09.png)

  

Keyfile başarılı olarak yüklendiğinde, ekranda adres ve bakiye bilgisinin yanı sıra SIN WebTool üzerinde Tam Kontrole sahip olduğunuza dair bir mesaj alacaksınız.



![](assets/img/sin_webtool_guide/webtool10.png)

  

# Gönderme
    

Soldaki menüden “Send” butonuna tıklayınız


![](assets/img/sin_webtool_guide/webtool11.png)

  

Coin Control açılır menüsünden istediğiniz miktarı seçin. Ya da Amount kısmına göndermek istediğiniz miktarı yazıp “Auto select coins” butonuna tıklayınız. Böylece göndermek istediğiniz miktar otomatik olarak seçilecektir. Bu esnada sağ üstte “Coin Control is Updated” mesajını görmelisiniz.


![](assets/img/sin_webtool_guide/webtool12.png)

  


Daha sonra Keyfile oluşturma aşamasında verdiğiniz şifreyi Passparase kutucuğuna giriniz ve **Verify Input** butonuna tıklayınız.


  
![](assets/img/sin_webtool_guide/webtool13.png)



**True** Mesajı işlemin başarılı olduğunu bize bildirir.

Şimdi SIN göndereceğimiz adresi girip “Create-Sign” butonuna tıklayabiliriz.


  
  
![](assets/img/sin_webtool_guide/webtool14.png)

İmzalama başarılı olduğunda, **Send** butonu ile gönderim işlemini tamamlayabilirsiniz.


![](assets/img/sin_webtool_guide/webtool15.png)

  


Bu işlem sonucunda sağ üstte **"Transaction is broadcasted to the network with success!"**  mesajı ile bilgilendirileceksiniz ve size işleme ait bir tx numarası verilecektir.



![](assets/img/sin_webtool_guide/webtool16.png)

  

# Payment
    

Bu özellik çok yakında çalışır hale gelecektir....


# R.S.V Vote
    

Bu özellik sayesinde mevcut oylamaya oy verebilirsiniz.

Soldaki menüden "R.S.V Vote" düğmesini tıklayın.

  

![](assets/img/sin_webtool_guide/webtool17.png)

  
  

1- Bir proposalID numarası giriniz. (Örnek: 10000000)

2- Oyunuz durumu için **Yes** yada **No** giriniz.

3- **Verify input** butonuna tıklayınız.

Bu oylama için sizden **1 SIN** talep edilecektir.

  


![](assets/img/sin_webtool_guide/webtool18.png)

  

Şifrenizi girdikten sonra  **Create-Sign** butonuna tıklayınız.

  

![](assets/img/sin_webtool_guide/webtool19.png)

  

![](assets/img/sin_webtool_guide/webtool20.png)

  

Oyunuz başarıyla gönderildikten sonra size bir İşlem Kimliği verilecektir.



![](assets/img/sin_webtool_guide/webtool21.png)



# Multisig Address
    

Çok yakında...



# Multisign Tx
    

Çok yakında...


# Proposal
    

Çok yakında...

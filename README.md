# Windows-Server-DFS-kurulumu-ve-yapilandirmasi
Windows Server 2019 , IIS sunucularında içerik senkronizasyonu için sıklıkla kullanılan bu yöntem ile iki web sunucusu arasında dosyalarınızı sync duruma getirebilirsiniz. DFS (distributed file system) replication yapısının kurgulanması için önerilen yapı 3
        sunucudan oluşmaktadır.
        <ol>
            <li>AD DS (active directory domain service) sunucusu </li>
            <li>DFS1 sunucusu (web server içeriğini sync edecekseniz IIS yüklü olması gerekmektedir.)
            </li>
            <li>DFS2 sunucusu (web server içeriğini sync edecekseniz IIS yüklü olması gerekmektedir.)
            </li>
        </ol>
        AD DS kurulumu sonrası web serverlarınızı domain controller üzerine member ediniz. İşlemleriniz tamamladıktan sonra DFS için planladığınız 1 ve 2nci sunucu için DFS kurulumuna başlayabilirsiniz. Ek bilgi:
        <ul>
            <li><a href="https://social.technet.microsoft.com/wiki/contents/articles/52623.powershell-ile-ad-ds-kurulumu-ve-yaplandrmas-tr-tr.aspx">AD DS kurulumu için tıklayınız.</a>
            </li>
            <li><a href="https://social.technet.microsoft.com/wiki/contents/articles/52833.powershell-ile-iis-kurulumu-tr-tr.aspx">IIS kurulumu için tıklayınız.</a>
            </li>
        </ul>
        <div>DFS replication ile dosya senkronizasyonu role kurulumu Windows Server işletim sistemi ailesinde "Roles and Features" bölümünde "File and Storage Services" altında bulunmaktadır. Kurulum için yapımda kurguladığım DFS1 ve DFS2 sunucuları için kurulum işlemine
        başlıyorum. Kurulumu iki sunucu içinde eş zamanlı olarak gösteriyor olacağım.</div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ1.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>DFS1 ve DFS2 sunucularımda Server Manager Dashboard üzerinden "Add roles and features" linkine basıyoruz.
        <br>
        </div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ2.png"><br>
        </div>
        <div><br>
        </div>
        <div>Add roles and feature penceresinde ilk adımımız "Before you begin" adımında next butonuna basarak devam ediyoruz.
        <br>
        </div>
        <div><br>
        </div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ3.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>"Select installation type" adımında "role-based or feature-based installation" seçerek next butonuna basıyoruz.
        <br>
        </div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ4.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>"Select destination server" adımında "select a server from the server pool" seçiyorum ve aşağıdaki DFS için ilgili sunucularımı seçiyorum.
        <br>
        </div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ5.png"><br>
        </div>
        <div><br>
        </div>
        <div>"Select server roles" adımında sağ bölümde bulunan roles kısmı altında bulunan "File and storage services" role genişletiyorum. "DFS replication" seçiyorum.
        <br>
        </div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ6.png"><br>
        </div>
        <div><br>
        </div>
        <div>"Add feature that are required for DFS replication?" bölümünde sağ alt bölümde bulunan "Add Features" tıklıyorum.
        <br>
        </div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ7.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>Server Roles adımını seçim işlemimi görüntüledikten sonra next butonuna basarak geçiyorum.
        <br>
        </div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ8.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>"Select features" adımında işlem yapmadan next butonuna basarak devam edebilirsiniz. İlgili features zaten role ile birlikte bir önceki seçim aşamasında tamamladık.</div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ9.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>"Confirm installation selections" adımında seçtiğimiz roles and features özetini görüntülüyoruz. "Restart the destination server automatically if required" seçeneğini seçiyorum. Kurulum sonrası işletim sistemi restart etmesi gerekiyorsa işlemi gerçekleştirmesi
        için. Son olarak Install butonuna basarak işlemimi tamamlıyorum. <br>
        </div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ10.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>Yüklem işlemi başlayacaktır. Installation progress ekranında Feature installation yükleme barı altında bulunan bölümde " Installation succeeded on &lt;server adı&gt; gördüğünüzde işlem tamamlanmıştır. Close butonuna basarak pencereyi kapatabilirsiniz. DFS1.eom.local
        ve DFS2.eom.local sunucularım için DFS replication role kurulumu tamamlanmıştır. DFS replication yapılandırması için seçtiğiniz bir sunucu üzerinde yapılandırma işlemlerine başlıyoruz. Ben yapılandırmaya DFS1.eom.local sunucum ile devam edeceğim bu işlemleri
        sadece seçtiğiniz DFS sunucusu üzerinde yapmanız yeterlidir. Start –&gt; Windows Administrative Tools –&gt; DFS Management uygulamasını açarak yapılandırma işlemlerimize başlıyoruz.</div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ13.png"><br>
        </div>
        <div><br>
        </div>
        <div>DFS Management penceremiz açılacaktır.</div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ14.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>DFS Management penceremizde sol bölümde bulunan replication menüsüne sağ tıklıyoruz. "New Replication Group" tıklıyoruz.
        <br>
        </div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ15.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>New Replication Group Wizard penceresinde "Replication Group Type" adımında "Multipurpose replicaiton group" seçiyoruz. Next butonuna basarak devam ediyoruz.
        <br>
        </div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ16.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>"Name and Domain" adımında replication için isim veriyoruz ve işlem yapacağımız domain seçiyoruz. Next butonuna basarak devam ediyoruz.
        <br>
        </div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ17.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>"Replication Group Members" adımında "add" butonuna basıyoruz ve DFS replication yapacağımız computer seçimini yapıyoruz.
        <br>
        </div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ18.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>DFS replication yapacağımız computer seçtikten sonra next butonuna basarak devam ediyoruz.
        <br>
        </div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ19.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>"Topology selection" adımında "Full Mesh" seçiyoruz next butonuna basarak devam ediyoruz.
        <br>
        </div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ20.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>"Replication group Schedule and bandwith" adımında full seçiyoruz ve next butonuna basarak devam ediyoruz.
        <br>
        </div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ21.png"><br>
        </div>
        <div><br>
        </div>
        <div>"Primary member" adımında işlem önceliği olan ve ana sunucu olarak kabul edilecek sunucuyu seçiyoruz.
        <br>
        </div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ22.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>"Folders to replicate" adımında "add" butonuna basarak sync etmek istediğimiz klasör yada klasörleri tanımlıyoruz. (Web uygulamanız için bu yapıyı oluşturuyorsanız web sitenizin olduğu klasörü seçiniz)</div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ23.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>Eklemiş olduğunuz klasör dizinleri için Local path yapılandırması yapıyoruz. Bu adımda DFS2 sunucumuzda bulunan sync olucak klasörleri seçiyoruz. Dikkat edilmesi gereken bir detay aynı dizin ve aynı isimde olması işinizi kolaylaştıracaktır. Ben iki dizin
        eklemiştim. Birincisi inetpub ve ekstra olarak test ozan şeklinde iki klasör bunlar için edit butonuna basarak tanımlamarımı yapıyorum.</div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ24.png">
        <img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ25.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>Adım adım sona yaklaşıyoruz. Review adımında yaptığımız işlemlerin özetini kontrol ediyoruz ve "Create" butonuna basıyoruz.
        <br>
        </div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ26.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>Confirmation adımında işlemlerimizin tamamlandığını görüntülüyoruz. Close butonuna basarak penceremizi kapatıyoruz. Yapılandırma işlemimiz tamamlanmıştır.</div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ27.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>Şimdi gerekli kontrollerimizi yapalım. DFS management altında replication bölümünde dfs-sync isiminde oluşturduğumuz replication tanımlamamızı görebilirsiniz.
        <br>
        </div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ28.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>Test için DFS1.eom.local sunucum üzerinde C:\OzanTest dizinine a ve b klasörlerini açıyorum. DFS2.eom.local sunucusunda da C:\OzanTest dizinine c klasörünü açıyorum. Replication için DFS managment dfs-sync bölümünden connection sekmesine geliyorum ve DFS
        1 sağ tıklayıp "replication now" butonuna basıyorum. <br>
        </div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ29.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>İsterseniz properties adımından replication süreçleirni Schedule olarak tanımlayabilirsiniz.
        <br>
        </div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ30.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>Successful gördükten sonra dosylarımızı kontrol ediyorum birkaç saniye gecikme yaşayabilirsiniz. Dosya boyutuna göre bu işlem biraz daha uzun sürebilir sabırlı olunduğu takdirde dosyların sync olduğunu göreceksiniz.</div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ31.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>DFS1.eom.local ve DFS2.eom.local sunucularımda C:\OzanTest dizinimi kontrol ediyorum. DFS1 den DFS2 ye a ve b klasörü DFS2 den de DFS1 sunucusuna c klasörünün sync olduğunu görebilirsiniz.</div>
        <div><br>
        </div>
        <div><img alt="" src="https://www.emreozanmemis.com/wp-content/uploads/2019/06/061819_1638_WindowsServ32.png">
        <br>
        </div>
        <div><br>
        </div>
        <div>DFS replication işlemimiz tamamlanmıştır. Umarım sizler için faydalı olmuştur.</div>
        <div><br>
        </div>
        <div>DFS replication yerine içerik senkrenizasyonu için robocopy komutunuda kullanabilirsiniz.
        <a href="https://social.technet.microsoft.com/wiki/contents/articles/53056.powershell-ile-robocopy-komutunun-kullanm-tr-tr.aspx">
        Robocopy komutunu incelelemek için tıklayınız. </a><br>
        </div>

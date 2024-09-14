Vagrant.configure("2") do |config|
  # اختيار صندوق Ubuntu (نظام التشغيل الافتراضي)
  config.vm.box = "ubuntu/bionic64"

  # إعداد الشبكة للسماح لك بالوصول إلى الخادم المحلي
  config.vm.network "private_network", ip: "192.168.33.10"

  # أوامر التثبيت التي سيتم تنفيذها عند تشغيل Vagrant
  config.vm.provision "shell", inline: <<-SHELL
    # تحديث النظام
    sudo apt-get update

    # تثبيت Apache و PHP
    sudo apt-get install -y apache2
    sudo apt-get install -y php libapache2-mod-php php-mysql

    # إعادة تشغيل Apache
    sudo service apache2 restart
  SHELL

  # مشاركة مجلد المشروع بين نظامك والمجلد الافتراضي
  config.vm.synced_folder ".", "/var/www/html"
end

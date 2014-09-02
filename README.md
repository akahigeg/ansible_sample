# 手順

MacOS X Marvericksにて

## VagrantとVirtualBoxのインストール

いずれも公式からパッケージを落としてきて入れる

* Vagrant 1.6.3
* VirtualBox 4.3.14r95030

## Vagrant

### boxファイルの追加

今回はDebian7.4を選んでみた

    vagrant box add debian74 http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_debian-7.4_chef-provisionerless.box

### 初期化

    mkdir ansible_sample
    cd ansible_sample
    vagrant init debian74

### Vagrantのネットワークの設定

* Vagrantfile
* ~/.ssh/config

## Ansibleのインストール

    pip install ansible

## Ansibleのテスト

## JenkinsをインストールするPlaybookの作成

provisioning/playbook_jenkins.yaml

## vagrant provision

ホストが見つからない問題があったがVagrantfileを以下のように修正して解決。

    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "provisioning/playbook_jenkins.yaml"
        ansible.inventory_path = "provisioning/ansible_hosts"
        ansible.limit = 'all'
    end

# Ansible雑感

* ベストプラクティスに従おうとすると結局ファイルが多くなって見通し悪くなるような
* ちょちょいっとしたものをちょちょいっと書けるのが魅力なのかな

以下の本のサンプルに書いてあったBetter Shell Scriptってのがしっくりきた。

http://tdoc.info/blog/2014/08/01/ansible_book.html

# 参考

* http://yutapon.hatenablog.com/entry/2014/04/08/102836
* http://momijiame.tumblr.com/post/78187543848/vagrant-ansible
* http://stackoverflow.com/questions/20801787/no-hosts-matched-issue-with-vagant-and-ansible
* http://docs.vagrantup.com/v2/provisioning/ansible.html
* http://qiita.com/soramugi/items/4b91222caaa67fb460f5
* http://d.hatena.ne.jp/hogem/20130615/1371306941


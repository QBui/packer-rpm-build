PACKER_VERSION="0.7.5"
RPM_RELEASE="1"
PACKER_ZIP="packer_#{PACKER_VERSION}_linux_amd64.zip"

desc "Clean the build workspace"
task :clean do
  `rm *.zip`
  `rm -rf usr/`
end

file PACKER_ZIP do
  system "wget https://dl.bintray.com/mitchellh/packer/#{PACKER_ZIP}"
end

task :extract => PACKER_ZIP do
  `mkdir -p usr/bin`
  `unzip #{PACKER_ZIP} -d usr/bin/`
end

desc "Build packer RPM"
task :build => :extract do
  `fpm --name packer --version #{PACKER_VERSION} --iteration #{RPM_RELEASE} -a x86_64 -t rpm -s dir ./usr`
end

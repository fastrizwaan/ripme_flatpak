
# ripme_flatpak
Ripme 

Java based flatpak, Ripme 

![](https://github.com/fastrizwaan/ripme_flatpak/blob/main/screenshot.png)

#### install flathub repo and freedesktop sdk 20.08
```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak install flathub org.freedesktop.Sdk/x86_64/20.08 runtime/org.freedesktop.Sdk.Extension.openjdk8/x86_64/20.08
```

#### clone and build flatpak from yaml
```
git clone https://github.com/fastrizwaan/ripme_flatpak.git
cd ripme_flatpak

# build
flatpak-builder --force-clean build-dir io.github.ripme.yaml

# install 
flatpak-builder --user --install --force-clean build-dir io.github.ripme.yaml

# run
flatpak run io.github.ripme
```

#### Build a flatpak bundle file from the above built repo:
```
flatpak-builder --repo="repo" --force-clean "build" io.github.ripme.yaml
flatpak --user remote-add --no-gpg-verify "ripme" "repo"
flatpak build-bundle "repo" "ripme.flatpak" io.github.ripme  --runtime-repo="https://flathub.org/repo/flathub.flatpakrepo"

flatpak --user install ripme.flatpak
flatpak run io.github.ripme
```


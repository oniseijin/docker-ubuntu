Kubectl Environment

This has the minimally useful environment for kubectl. It doesn't go too crazy with customizations as this is meant to be useful for CKAD/CKA tests, plus have a few value added


Very Minimal (what you can remember to do yourself) would be

.vimrc
===

```bash
set expandtab
set tabstop=2
```

.bashrc
===

```bash
export do="--dry-run=client -o yaml"
source <(kubectl completion bash)
```



Power Vim
===

 * https://octetz.com/docs/2020/2020-01-06-vim-k8s-yaml-support/


 Run following commands from within Vim to get this going. Unclear how to do this outside earlier

 :PlugInstall
 :CocInstall coc-yaml
 :CocConfig (already done for kubernetes)

 This is built from kubectl-ubuntu as I probably want that stuff too, but could be from straight ubuntu


 These will be combined to be a very rich kubernetes developer enviroment, but keeping separate for now


 Kubectl Max
 ===

 Has everything from the above, plus all useful configurations
 
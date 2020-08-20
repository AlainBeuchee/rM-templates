# rM-templates
Templates for reMarkable tablet.  
Suppose our template is Kanban_fr.png.  
Put your terminal in working directory were is the template 'Kanban_fr.png'.  

# Templates preparation  
## convert and resize  
- ratio 3:4 i.e. 1404x1872 centered and filled with a white background    

```sh
magick Kanban_fr.jpg -resize 1404x1872 -background white -compose Copy -gravity center -extent 1404x1872 -unsharp 0x1 -quality 92 template.png; open Kanban_fr.png
open Kanban_fr.png  
```
## convert png en svg  
- no command line solution to convert png to svg
- open Inkscape  
1 - File / Document property (^+cmd+D) / page / Arch B  
2 - open Kanban_fr.png   
3 - save as Kanban_fr.svg   

# Templates export and configuration  
## copy files from mac to rM  
```sh
scp Kanban_fr.png root@192.168.1.20:/usr/share/remarkable/templates/Kanban_fr.png  
scp Kanban_fr.svg root@192.168.1.20:/usr/share/remarkable/templates/Kanban_fr.svg  
```

## update of configuration file '.json'  
- connect rM tablet via wifi (check id with arp -a)  
```sh
ssh root@192.168.1.20 
```
- connect rM tablet via usb cable
```sh
ssh root@10.11.99.1 
```
- open .json file with nano
```sh
nano /usr/share/remarkable/templates/templates.json
```
- paste at the en of the configuration file (juste before '] }' ) the following lines
```
,
    {
      "name": "Kanban 4",
      "filename": "Kanban_fr",
      "iconCode": "\ue9db",
      "categories": [
        "Perso"
      ]
    }
```
- don't give the same name "name" for different templates
- the same icon may be used for several templates
- for organisational template use icons "\ue9dc" "\ue9da" "\ue9db"
- save and close  
^O ^X
- reboot reMarkable tablet

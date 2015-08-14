# Paquet bower fournissant le plugin lang-fr à tinymce

## installation

    $ bower install tinymce-lang-fr

C'est un module open source, donc pas besoin de deploy-key ssh (gitlab public project)

## configuration du projet qui dépend de tinymce

Dans le fichier `.bowerrc` s'il existe, sinon le créer, ajouter un script postinstall:

    ```json
    {
      "name": "tinyclient-xyz",
      "verion": "a.b.c",
      "scripts": {
        "postinstall": "./hooks/bower-post-install.sh >> .hooks.log"
      }
    }
    ```

Dans le répertoire du projet, créer un répertoire `hooks`

    $ mkdir hooks

Puis y créer le fichier suivant `bower-post-install.sh`

    $ nano hooks/bower-post-install.sh

Avec comme contenu

    ```sh
    #!/bin/sh
    echo "mkdir public/lib/tinymce/langs ..."
    mkdir public/lib/tinymce/langs
    echo "chdir public/lib/tinymce/langs ..."
    chdir public/lib/tinymce/langs
    echo "creating tinymce-lang-fr/fr_FR.js link ..."
    ln -s ../../tinymce-lang-fr/fr_FR.js .
    ```

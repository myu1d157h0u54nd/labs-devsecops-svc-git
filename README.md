# labs-devsecops-svc-git

que es git?

sistema de almacenamiento de codigo
  git
    sistema de almacenamiento en la nube
      github, proveedor
      gitlab,
        ellos se encargan de la infra
        te da una version de comunidad, para que vos instales y cuides tu server de repositorio de codigo
      bitbucket

# trabajo diario:

## trabajo local en sus equipo como mantenedores de codigo, git:

herramienta de cli: githttps://github.com/Dylan010/labs-devsecops-svc-git

1. ambiente de trabajo:
   /codigo_proyecto/
   index.html
   README.md
2. configuracion de git:
   a. configurada en local, la cuenta email de github o del repositorio
   b. creacion y configurado la key ssh
   1. en local
   2. y en la nube de github
3. c. configurada la key gpg
   1. creacion y configuracion
      1. en local
      2. en la nube de github
4. proceder con el flujo de trabajo:
   equipo de frontend:
   a. actualizar titulo de README
   b. cambiar el header del index.html
   equipo de backend:
   a. cambiar llamadas de api y backend en index.html
5. trabajo con git para resolver rutinas:equipo N:
   conseguir la ultima version del repositorio:
   git pull # traer todo el repo de la nube a mi local
6. entendiendo un repositorio y sus versiones (branch)
   a. es un almacen de codigo
   b. almacena en simultaneo varios versiones, presentes y pasadas de cada cambio historico.
   c. para esto usa algo llamado branch
   d. uso de git sobre un ambiente de trabajo

almacenes:

/codigoProyecto:

    README.md

/.codigoProyecto

    /.git/ repo - local

    copia local del ultimo estado de la nube de:

    README.md


  flujo de procesos en repos git:

    bajar ultima version del codigo

    modificar o hacer agregados el codigo

    agregar a lista de trabajo de git

    almacenar al reposirotio local

    enviar copia del repositorio local, al repositorio en la nube

    validar que no haya colisiones


propuesta de flujo de trabajo con git, usando gitflow

## seguridad en GIT y GITHUB:


## Claves de firmado gpg para commit en git:

    GPG es un derivado de PGP, es una tecnologia de encriptacion y firmado digital.
    metodos de encriptacion:
        simetrico
            material a encriptar (cifrar) + clave unica = meterial encriptado (crifrado)
            si persona A, quiere encriptar algo para persoba B, ambos deben conocer la clave
            cadena decustodia de la clave
            y genera problemas cuando persona C, tambien precice acceso
        asimetrico
            proceso de cifrado:
                material a cifrar + clave de cifrado (publica de persona X) = material cifrado
            proceso de descifrado:
                material cifrado + clave privada (clave privada de persona X) = material sin cifrar original


Firmado de commit en git:
    1 que es un commit?
        1 label, o tag,
            coordenadas de lamacenado de cambios en el codigo:
                id md5 para identificar dentro del almacen
        1 listado de archivos que se modificaron y alamcenaron dentro del amacen de git
        1 msg de resumen el detalle del trabajo guardado
        Author:, el id md5, se firma con la clave gpg publica del author

### GPG:

Crear nuevas claves gpg
gpg --full-generate-key

Verificar llaves locales creadas:
gpg --list-secret-keys --keyid-format=long
/Users/hubot/.gnupg/secring.gpg
------------------------------------
sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
uid                          Hubot <hubot@example.com>
ssb   4096R/4BB6D45482678BE3 2016-03-10


Exportar clave publica para usar en GitHub:
gpg --armor --export 3AA5C34371567BD2

Copia la clave de GPG, que empieza por -----BEGIN PGP PUBLIC KEY BLOCK----- y termina con -----END PGP PUBLIC KEY BLOCK-----.

Validar configuracion de git:
git config --lis

Configurar git para usar clave gpg:
git config --global --unset gpg.format
git config --global user.signingkey 3AA5C34371567BD2
git config --global commit.gpgsign true
[ -f ~/.bashrc ] && echo -e '\nexport GPG_TTY=$(tty)' >> ~/.bashrc




### Docus de GitHub:
https://docs.github.com/es/authentication/managing-commit-signature-verification/checking-for-existing-gpg-keys
https://docs.github.com/es/authentication/managing-commit-signature-verification/generating-a-new-gpg-key
https://docs.github.com/es/authentication/managing-commit-signature-verification/adding-a-gpg-key-to-your-github-account



## Claves de coneccion ssh para comunicacion con GitHub:

Ver en local las claves ssh:
ls ~/.ssh/

Generar claves nuevas:
ssh-keygen -t ed25519 -C "lastra.nikos@gmail.com" -f ~/.ssh/id_ed25519_?idUser?
    [-t dsa | ecdsa | ecdsa-sk | ed25519 | ed25519-sk | rsa]
        https://ed25519.cr.yp.to/
    [-C comment]

Agregar la llave nueva al agente ssh-agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

Agregar la llave ssh en GitHut

Prueba de coneccion ssh contra GitHub:
ssh -T git@github.com
ssh -T -v git@github.com

## trabajo en el sistema de repocitorio: github

requisitos:
  basicos que tienen la mayoria:
    1 cuenta de usuario:
  requisitos de seguridad:
    * hablitacion de 2do factor de autenticacion:
      google autenticator
      u otras, keeweb (almacen de claves local y en la nube como dropbox u otros datastorage)
    * key-ssh
    * key gpg

## Test fork and pull request

El alumno dylan estuvo aqui 
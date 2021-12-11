Autor: Hernan Moreno

Twitter: [https://twitter.com/HernnMoreno18](https://twitter.com/HernnMoreno18)

Web: [https://www.hmoreno.dev/](https://www.hmoreno.dev/)

## Comandos importantes

mkdir → Crea carpeta

touch archivo.txt → Crea Archivo "archivo.txt"

car archivo.txt → Muestra contenido de archivo plano

history → Muestra listado de comandos digitados

rm archivo.txt → Elimina archivo

```jsx
git log —all —graph —decorate —oneline
```

Muestra historia de los cambios realizados "commit"

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1be57636-7286-4729-84d0-b7c5f43c1b98/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1be57636-7286-4729-84d0-b7c5f43c1b98/Untitled.png)

## Creación de alias

```jsx
alias arbolito="git log —all —graph —decorate —oneline"
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9d1f2dbf-9d76-45b6-8e52-34f23565281e/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9d1f2dbf-9d76-45b6-8e52-34f23565281e/Untitled.png)

## Tags

```jsx
git tag
```

Muestra las versiones de tag creadas

```jsx
git show-ref —tags
```

Muestra la relación entre tag y commit

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7a85b03d-d5cf-4f56-af1d-e7647d470b87/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7a85b03d-d5cf-4f56-af1d-e7647d470b87/Untitled.png)

Para poder subir tags creados

```jsx
git push origin --tags
```

Eliminar tag

```jsx
git tag -d [NombreTag]
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5594e06d-9235-4abd-abcb-fe8820e41e6b/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5594e06d-9235-4abd-abcb-fe8820e41e6b/Untitled.png)

De esta forma eliminas el tag de manera interna (Mi repositorio).

Para eliminar el tag remoto es necesario realizar el siguiente comando:

```jsx
git push origin :ref/tags/dormido
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/80894f74-9536-414d-a325-3d2762056642/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/80894f74-9536-414d-a325-3d2762056642/Untitled.png)

## Configuración

Para poder ver la configuración

```jsx
git config -l
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f02fa6fd-bbea-447d-9ae6-1c790bb5f267/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f02fa6fd-bbea-447d-9ae6-1c790bb5f267/Untitled.png)

Para poder cambiar el correo dentro de mi configuración

```jsx
git config --global user.email "[Correo]"
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/902a79d6-d903-4746-b3e5-071d6668d32f/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/902a79d6-d903-4746-b3e5-071d6668d32f/Untitled.png)

## Crear llave SSH

Para poder crear la clave ssh primero hay que posicionarse en nuestro home (~). Para poder ver nuestra ubicación pueden utilizar el comando pwd

```jsx
pwd
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/46f36e8e-31c0-493f-a86c-c485ddf00d3c/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/46f36e8e-31c0-493f-a86c-c485ddf00d3c/Untitled.png)

El comando para crear nuestra clave ssh es ssh-keygen, junto con los parámetros: -t aquí ponemos el algoritmo de encriptación que queremos en este caso ocuparemos la más común que es RSA, -b aquí vamos a especificar que tan compleja es la llave, seguido de -C aquí vamos a poner el email al que se va a configurar la llave.

```jsx
ssh-keygen -t rsa -b 4096 -C "[Correo]"
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bae00b5d-3ce4-4a52-bf60-0d36c413b8d1/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bae00b5d-3ce4-4a52-bf60-0d36c413b8d1/Untitled.png)

Para confirmar que la llave ssh esta agregada al entorno se confirma con:

```jsx
eval $(ssh-agent -s)
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3166eac6-f016-4853-9faf-b9f2bad8af0b/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3166eac6-f016-4853-9faf-b9f2bad8af0b/Untitled.png)

Para agregar la llave a git publica con ssh-add [ruta llave publica]

```jsx
ssh-add ~/.ssh/id_rsa
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/876d8d60-3941-429d-898b-4e9d7759a156/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/876d8d60-3941-429d-898b-4e9d7759a156/Untitled.png)

## Comandos y recursos colaborativos en Git y GitHub

- **git shortlog -sn** = muestra cuantos commit han hecho cada miembros del equipo.
- **git shortlog -sn --all** = muestra cuantos commit han hecho cada miembros del equipo hasta los que han sido eliminado
- **git shortlog -sn --all --no-merge** = muestra cuantos commit han hecho cada miembros quitando los eliminados sin los merges
- **git blame ARCHIVO** = muestra quien hizo cada cosa linea por linea
- **git COMANDO --help** = muestra como funciona el comando.
- **git blame ARCHIVO -Llinea_inicial,linea_final**= muestra quien hizo cada cosa linea por linea indicándole desde que linea ver ejemplo -L35,50
- *git branch -r **= se muestran todas las ramas remotas
- **git branch -a** = se muestran todas las ramas tanto locales como remotas

## Creación de alias

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9569a312-956d-4bf1-b187-b786cf57101b/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9569a312-956d-4bf1-b187-b786cf57101b/Untitled.png)

---

## Como salir del editor VIM

esc+shift+z+z

[Cuestionario Tipo](https://www.notion.so/Cuestionario-Tipo-24b1d9db45eb45c1952cab8f8e77a1c4)

## Como ver la ruta URL de mi repositorio

```tsx
git remote -v
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3dd513ef-bdd5-48ca-a045-2f517eff2b7e/Untitled.png)

Como cambiar la URL de mi repositorio

```csharp
git remote set-url origin git@github.com:Hmoren/template2.git
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/31f4697d-b7e0-4f1b-998f-8eb6a3ce4dc7/Untitled.png)

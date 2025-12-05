# Symfony 7.4 LTS installation rapide

## Installation

```bash
symfony check:requirements
```

Si pas de soucis :

```bash
symfony new Sym74LTS --webapp --version=lts

cd Sym74LTS

symfony serve
```

### Création d’un contrôleur :

```bash
php bin/console make:controller
> BlogController
> yes
```

Dans `src/Controller/BlogController.php` :

```php
### ...
final class BlogController extends AbstractController
{
    #[Route('/', name: 'homepage')]
    public function index(): Response
    {
        return $this->render('blog/index.html.twig', [
            'controller_name' => 'BlogController',
        ]);
    }
}
```

### Installation de PHP CS Fixer

```bash
composer require --dev friendsofphp/php-cs-fixer
```

Pour l'appliquer

```bash
./vendor/bin/php-cs-fixer fix
```

### Utilisation de MariaDB

Dans `config/packages/doctrine.yaml`

```bash
        identity_generation_preferences:
            # commentez cette ligne et mettre MariaDBPlatform
            #Doctrine\DBAL\Platforms\PostgreSQLPlatform: identity
            Doctrine\DBAL\Platforms\MariaDBPlatform: identity
```

Création de .env.local :

```bash
cp .env .env.local
# puis créer une clef
php -r 'echo bin2hex(random_bytes(32));'
```

Dans .env.local :

```bash
# la clef
APP_SECRET=d09c63192a0539a36452ae21b489544d870d3767ec98a19744b5050ea0adbe72
# la base de donnée avec MariaDB en local (modifiez
# les paramètres de connexion)
DATABASE_URL="mysql://root:@127.0.0.1:3307/blog_name?serverVersion=11.4.9-MariaDB&charset=utf8mb4"
```

Vérifiez que votre serveur MariaDB est lancé, puis créez la DB

```bash
php bin/console doctrine:database:create
```

### Création des entités

Pour le schéma voir votre DB ou comme exemple :

[exemple DB](https://github.com/WebDevCF2m2025/symfony-7-2025/blob/main/partie3/db11.md)

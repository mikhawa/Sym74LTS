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

Création d’un contrôleur :

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

Installation de PHP CS Fixer

```bash
composer require --dev friendsofphp/php-cs-fixer
```

Pour l'appliquer

```bash
./vendor/bin/php-cs-fixer fix
```

# Symfony 7.4 LTS installation rapide

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

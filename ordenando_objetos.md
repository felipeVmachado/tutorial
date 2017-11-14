# Ordenando objetos

Um QuerySet também nos permite ordenar a lista de objetos. Vamos tentar ordenar as postagens pelo campo `created_date`:

    ``` >>> Post.objects.order_by('created_date') ```
    [<Post: Título da amostra>, <Post: Postagem número 2>, <Post: Minha 3ª postagem!>, <Post: 4ª Postagem do Título>]

Você também pode inverter a ordem adicionando um `-` no início:

      ``` >>> Post.objects.order_by('-created_date') ``` 
      [<Post: 4ª Postagem do Título>,  <Post: Minha 3ª postagem!>, <Post: Postagem número 2>, <Post: Título da amostra>]

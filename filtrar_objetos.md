# Filtrar objetos

Os QuerySets são muito usados pela habilidade de filtrar objetos. Digamos que queremos encontrar todos as postagens escritas pela usuária Ana. Nós usaremos o `filter` em vez de `all` em `Post.objects.all()`. Entre parênteses indicamos as condições que precisam ser atendidas por uma postagem de blog para que ela entre em nosso queryset. Em nosso caso, a condição é que `author` deve ser igual a `me`. A maneira de escrever isso no Django é: `author=me`. Agora o nosso trecho de código parece como este:

    ``` >>> Post.objects.filter(author=me) ```
    [<Post: Título da amostra>, <Post: Postagem número 2>, <Post: Minha 3ª postagem!>, <Post: 4º Título da Postagem>]
    
 Ou talvez nós queiramos ver todas as postagens que contenham a palavra 'Título' no campo de `Título`?
 
      ``` >>> Post.objects.filter(title__contains='Título') ```
      [<Post: Título da amostra>, <Post: 4º Título da Postagem>]
      

        Nota Existem dois caracteres de sublinhado (`_`) entre o `title` e `contains`. Django ORM usa esta sintaxe para separar nomes de campo ("title") e operações ou filtros ("contains"). Se você usar apenas um sublinhado, você obterá um erro como "FieldError: Cannot resolve keyword title_contains".

Você também pode obter uma lista de todas as postagens publicadas. Fazemos isso filtrando todos os posts com `published_date` definido no passado:

      ``` >>> from django.utils import timezone ```
      ``` >>> Post.objects.filter(published_date__lte=timezone.now()) ```
      []

Infelizmente, nenhuma de nossas postagens feitas a partir do console do Python estão publicadas ainda. Mas nós podemos mudar isso! Primeiro obtenha uma instância de uma postagem que queremos publicar:

      ``` >>> post = Post.objects.get(title="Título da amostra") ```
      
      
E então vamos publicá-la com o nosso método `publish`!

      ``` >>> post.publish() ```

Agora, tente obter a lista de postagens publicadas novamente (pressione o botão da seta para cima 3 vezes e tecle `enter`):
 
      ``` >>> Post.objects.filter(published_date__lte=timezone.now()) ```
      [<Post: Título da amostra>]
      
      Detalhe:
      O timezone é responsável por fazer com que o horário da publicação fique de acordo com o time_zone de onde utilizado na aplicação.

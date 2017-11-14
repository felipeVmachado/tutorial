# Criando um objeto

É assim que você cria um objeto Post no banco de dados:

     ``` >>> Post.objects.create(author=me, title='Título da amostra', text='Teste')  ```

Mas aqui temos um ingrediente que está faltando: `me`. Precisamos passar uma instância do modelo `User` como autor. Como fazer isso?

Primeiro vamos importar o modelo User:

    
    ``` >>> from django.contrib.auth.models import User ```

Quais usuários temos no nosso banco de dados? Experimente isso:

    
    ``` >>> User.objects.all() ```
    <QuerySet [<User: Ana>]>

É o superusuário que criamos anteriormente! Vamos obter uma instância de usuário agora:

    ``` me = User.objects.get(username='Ana') ```

Como você pode ver, nós agora usamos um `get` para pegar um `User` com um `username` igual a 'Ana'. Claro, você tem que adaptar essa linha ao seu nome de usuário.

Agora finalmente podemos criar nossa primeira postagem:

    ``` >>> Post.objects.create(author=me, title='Título da amostra', text='Teste') ```
    
Viva! Quer ver se funcionou?

    ``` >>> Post.objects.all() ```
    <QuerySet [<Post: meu título de postagem>, <Post: outro título de publicação>, <Post: Título da amostra>]>
  
  Ai está, mais uma postagem na lista!

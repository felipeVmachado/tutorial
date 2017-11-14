# Encadeando QuerySets

Você pode também combinar QuerySets pelo `encadeamento` deles em sequência:

      ``` >>> Post.objects.filter(published_date__lte=timezone.now()).order_by('published_date') ```

Isso é realmente poderoso e permite que você escreva pesquisas ("queries") bem complexas.

Legal! Você já está pronto(a) para a próxima parte! Para fechar o terminal digite:

      
      ``` >>> exit() ```
      $

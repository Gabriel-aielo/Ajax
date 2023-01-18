Esta pasta contém estudos relacionados ao AJAX.

AJAX - Asynchronus JavaScript and XML - JavaScript e XML Assíncronos

Toda navageção entre páginas é feita de forma síncrona, ou seja, ao se clicar em um link (botão) ou qualquer redirecionamento uma página para outra, esta é requisitada no servidor alocado. A1 requisição e a resposta retornada pelo servido pode demorar milisegundos ou segundos... a demora do retorno da resposta torna a navegação lenta, impactando o usuário.

A solução deste problema é o AJAX. Ao ser solicitado o acesso de determinada página, ela não permanece estática, mas sim dinâmica. Quando ocorre o retorno pelo servidor, não ocorre o "re-fresh" dá pagina, mas sum uma atualização dinamica do conteúdo que foi solicitado, enquanto o restante da página permanece estático.

Exemplo:
Imagine a ferramenta de sugestões de pesquisa do Google. Ela ajuda a completar as palavras que você digita em tempo real enquanto a página permanece estática.

No início dos anos 90, quando a internet ainda não era tão avançada, a mesma funcionalidade iria exigir que a página fosse recarregada sempre que uma nova sugestão de pesquisa aparecesse na tela. O AJAX permite a troca de informações simultânea sem interferir com outras funções.



Código na prática:

----------------------------------------------------MÉTODO "OPEN" E "SEND"--------------------------------------------

    1. Uma tag HTML possui o evento onclick, nota-se que o atributo "href" não realiza a função de redirecionamento da página.

            <a href="#" class="btn btn-primary" onclick="requisitarPagina('pagina_1_conteudo.html')" >Página 1</a>

    2. Desenvolvendo os comando "new XMLHttpRequest()" dentro de uma função, a requisição só é realizada quando o evento "onclick" for executado.

            function requisitarPagina(url){                
                let ajax = new XMLHttpRequest(); //variável com armazenamento do ajax

                ajax.open('GET', url) //requisição atraq´ves do método "GET", para a página "pagina_1_conteudo.hmtl")
                ajax.send() //Envia a requisição

                console.log(ajax)
            }

----------------------------------------------------Anotações--------------------------------------------

Status != State

//acesse a imagem "exemplo1.png";
//acesse a imagem "exemplo2.png"

*State* é o estado de prontidão em que a resição se encontra:

Estado de Prontidão 0: Quando cria-se o objeto de solicitação ele está no estado 0. Para o exemplo anterior é quando a variável request chama open.

Estado de Prontidão 1: Aqui diz-se que está no estado 1 quando a solicitação sabe como e com o que se conectar. Para o exemplo anterior é quando a propriedade onreadystatechange é configurada.

Estado de Prontidão 2: Nesse estado a solicitação está em progresso, portanto o servidor já recebeu a solicitação no script e esse programa responde essa solicitação.

Estado de Prontidão 3: No estado 3 os dados estão sendo baixados no objeto de solicitação, mas ainda não estão prontos para serem usados no código. O navegador ainda está capturando a resposta do servidor.

Estado de Prontidão 4: No estado 4 a resposta do servidor está concluída. Agora tem-se todos os dados da resposta disponíveis na propriedade responseText do objeto de solicitação. Nesse instante a propriedade onreadystatechange é executada e já pode usar os dados do servidor.



Read more: http://www.linhadecodigo.com.br/artigo/3587/ajax-basico-estado-de-prontidao-e-codigo-de-status.aspx#ixzz7ql3zKLiO

*Status* é a informação retornada pelo servidor, um código gerado que informa a situação final da requisição, seja ela concluida com sucesso ou com falha.

Página de verificação dós códigos de retorno: https://developer.mozilla.org/en-US/docs/Web/HTTP/Status



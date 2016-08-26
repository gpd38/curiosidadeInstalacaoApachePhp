# Projeto 09: Instalação e configuração do apache e do php em um computador windows

Projeto criado para documentar a experiência de instalar o apache e o php 7 manualmente, pois não desejo utilizar os pacotes como xampp, wamp entre outros.

Apache: É um servidor WEB responsável pela publicação de documentos, imagens ou qualquer outro objeto que venha a ser acessado por um cliente através de um navegador.

PHP: É uma linguagem de script open source de uso geral, muito utilizada, e especialmente adequada para o desenvolvimento web e que pode ser embutida dentro do HTML.

### Download

Acesse o site do [apache](http://httpd.apache.org/download.cgi) e faça o download da ultima versão de acordo com seu SO (32 bits ou 64 bits). A versão que foi utilizada neste projeto para teste foi a [apache lounge - 64 bits](https://www.apachelounge.com/download/).

Acesse o site do [php](http://php.net/downloads.php) e faça o download da ultima versão de acordo com seu SO (32 bits ou 64 bits). A versão que foi utilizada neste projeto para teste foi a [php7-64 bits - Thread Safe](http://windows.php.net/downloads/releases/php-7.0.10-Win32-VC14-x64.zip).

### Instalação e configuração

1. Extraia o apache para o diretório c:\apache24
2. Abra o arquivo httpd.conf que esta localizado na pasta c:\apache24\conf
3. Acrescente as linhas abaixo no final do arquivo
```
LoadModule php7_module "c:/php7/php7apache2_4"
AddHandler application/x-httpd-php .php
PHPIniDir "c:/php7"
<FilesMatch \.php$>
    SetHandler application/x-httpd-php
</FilesMatch>
```
4. Extraia o php para o diretório c:\php7.
5. Copie o arquivo php-ini-development e renomeio para php.ini.
6. Abra o arquivo php.ini que está localizado na pasta c:\php7\php.ini.
7. Para habilitar qualquer extensão do php você deve remover o "ponto e vírgula" do início da linha. Procure por "pdo_mysql.dll" que está localizado próximo a linha número 883. Remova o "ponto e vírgula" do início da linha.
```
extension=php_pdo_mysql.dll
```
8. Para habilitar o diretório das bibliotecas do php procure por "extension_dir" que está localizado próximo a linha número 724. Altere o diretório ext para "c:\php7\ext" que foi onde descompactamos o php7. Deve ficar como o código abaixo.
```
; extension_dir = "./"
; On windows:
extension_dir = "c:\php7\ext"
```
9. Acesse a pasta c:\apache24\bin e crie um atalho do arquivo "ApacheMonitor.exe" em sua área de trabalho.
10. Execute o arquivo e clique em "Start" para iniciar o servidor apache.
11. Acesse o navegador e digite "localhost".

Se tudo estiver configurado corretamente, deve aparecer uma página escrita "It works!"

### Onde publicar

Todos os arquivos html ou php devem ser salvos no diretório c:/apache24/htdocs para que o servidor tenha acesso e você possa testar em seu navegador.


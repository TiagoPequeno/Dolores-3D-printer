# Dolores-3D-impressora
Trabalhos iniciais realizados com a impressora roots do professor Orivaldo na inPACTA

1. De inicio pratiquei bastante os comandos de navegação e movimentação com a prusa nos eixos XYZ, e fui aprendendo a regular o nivelamento da mesa com o bico;

2. Até descobrir qual a melhor técnica de ajuste para o nivelamento, passei por várias situações de retirar o calibre e colocar novamente;

3. Os vídeos
	https://www.youtube.com/watch?v=lDNCkiZAV5c ;
	https://www.youtube.com/watch?v=PdRKd4CL4VU ;
	https://www.youtube.com/watch?v=5vBgvep8vUo ;
	https://www.youtube.com/watch?v=ArvamVNCteY ;
ajudaram a entender.

4. É muito importante compreender a função do fim de curso (end stop), principalmente do eixo Z, no ajuste de nivel e calibre da mesa;

5. Atualização do firmware:

	Para realizar a mudança na programação da impressora, foi necessario acessar a página Github de seu criador: 	https://github.com/lar-ect/impressoras-3d (1) onde é possivel encontrar o repositorio completo de tudo sobre impressão 3D bem refinado, inclusive um aprofundamento sobre a técnica de auto nivelamento da mesa de impressão em formato tutorial;
	
	A alteração é feita no arquivo Marlin, aberto pela IDE do Arduino (arquivo em formato .ino), do conjunto controlador da impressora que pode ser acessado em https://drive.google.com/open?id=0B7yvZReRz0z6RjZpb1BrNDZRWXc (2)
(Aqui está o arquivo completo de uso geral em qualquer impressora 3D, sendo necessario definir os parametros especificos da máquina a qual será controlada pelo código encontrado nesse compartilhado);
	As modificações necessarias para Dolores estão registradas no repositorio: https://github.com/orivaldosantana/impressoras-3d/blob/master/CONFDolores.md (3), mas ficou faltando informar qual o dispositivo (board) que seleciona a referencia dessa máquina, caso seja carregado o Marlin de (2), e isso só foi percebido no vídeo https://www.youtube.com/watch?v=cpyZGah5Ct4, indicado pelo professor para servir de auxilio no procedimento de atualização do firmware, já que Dolores não respondia mais aos comandos do Pronterface após o upload do programa com as alterações que indica o repositorio.
	A alteração é feita na aba configuration.h
	E o Marlin que foi carregado inicialmente foi o GERAL, apenas com os parametros de (3) alterados nele (isso pode ter gerado problemas na movimentação durante o trabalho de impressão - Confirmando...); 
	Como medida de garantia e segurança, tinhamos um firmware de Dolores de sua ultima atualização antes de trocar o bico e a estrutura original do extrusor: https://drive.google.com/drive/folders/0B7yvZReRz0z6Ym5QbVUzcHdIQVE (4). Ao baixar esse arquivo, é preciso colocar tudo em uma mesma pasta (sketch). Ao tentar abrir o arquivo Marlin.ino , a IDE do Arduino vai sugerir que se crie tal pasta, porém apenas o arquivo .ino será colocado lá, sendo necessario mover o restante.
	Além disso o arquivo termistortables.h parece ser incompativel com a placa Arduino Mega que Tiago trouxe em 5/11, depois que a original de Dolores parou de comunicar semanas antes.
	Foi observado também um problema no momento de conectar a impressora pelo Pronterface, onde após várias tentativas o próprio programa apontou uma falha na taxa de tranferência de dados (boundrate) - (TENTAR RECUPERAR OS PRINTS NO PC QUE DEU PROBLEMA)

6. ajuste do extrusor;
	
	Um aperto excessivo no parafuso chave L (alien) do mecanismo extrusor estava comprometendo a qualidade da impressão, fazendo com que fosse depositado menos material e deixando as peças todas esponjosas, pois o filamento acabava ficando muito fino. O professor Orivaldo observando o trabalho do motor Nema ligado ao extrusor, folgou o parafuso enquanto Dolores imprimia uma peça e observamos que a qualidade da impressão melhorou consideravelmente, assim como ofluxo de trabalho do filamento sendo guiado pelo mecanismo do extrusor; (INCLUIR FOTOS)
	
7. alinhamento dos motores de Z e barulho no movimento de retração vertical;

	Confirmando se o barulho foi causado pela Marlin GERAL alterado que foi carregado no Mega que parou de comunicar;
	O Marlin de Dolores parece não carregar esse defeito, pois deve estar melhor ajustado pra ela nesse sentido;
	
8. Impressão da peça que substituiu a engrenagem do extrusor e bico antigos;

	https://www.thingiverse.com/thing:1182119 A peça ficou perfeitamente ajustada, a impressão ótima
	Modelar um peça para a Ventoinha que resfria a peça e Fitas de Led doadas por Tiago para iluminar a impressão;
	
9. Problema com fuga de corrente, aterramento e possivel queima do CI de comunicação serial no Arduino Mega controlador de Dolores;

	No dia 28/10, Dolores estava muito bem, realizando várias impressões. Até que durante a impressão de uma peça o Pronterface travou, mas a impressão continuou, então depois de muito tempo com o Pronterface travado o computador apagou e quando voltou, deu um diagnostico que o driver de vídeo dele havia se recuperado de uma falha, e foi quando Dolores parou de imprimir ficando com a peça presa na mesa. O computador não reconhece mais o Arduino Mega. Após várias tentativas de restabelecer comunicação e voltar a controlar a impressora, reinstalando o driver manualmente (Um dos erros reportados: Este dispositivo está desabilitado porque o firmware do dispositivo não lhe forneceu os recursos necessários. (Código 29)), trocando cabo USB, tentando reparar o PC, conectando em outro computador, confirmo a suspeita que o CI de comunicação serial do Arduino Mega queimou.
	Trocamos a placa Arduino Mega que controlava Dolores por outra e ela voltou a funcionar. Realmente a placa anterior, parece ter queimado o CI FTDI de comunicação serial. Farei uma tentativa de trocar esse CI para confirmar se foi esse o problema e reporto o resultado. (INCLUIR FOTOS). Mas por agora o novo Mega está funcionando perfeitamente, e o sistema Dolores + PC da inPACTA + Fonte de Dolores ligados em uma regua de linha e estabilizador de tensão, TUDO PERFEITAMENTE ATERRADO, ainda não resultou em choque eletrico;

10. Trocar o Mega e carregar qual dos dois Marlin? Sugestão... carrega um e testar, carrega o outro e testar... ;)
	
	Dolores voltou a funcionar com o Marlin dela, configurado por (3) + o arquivo thermistortables.h do Marlin GERAL (2), pois esse mesmo arquivo no repositorio de Dolores (4) está dando erro ao compilar.
	Primeiro teste: Marlin de Dolores + arquivo thermistortables.h do Marlin GERAL - Executando;
		Resultados: Dolores parece ter parado de "gritar" quando realiza saltos de um ponto a outro da peça sendo 			impressa (Verificando se isso se mantem);
	Segundo teste: Marlin Geral com configurações para Dolores - A executar;
		Resultados: Observar se assim o barulho dos saltos volta a atacar;
		
11. Os drivers para o novo Mega acoplado dia 5/11 na Dolores devem ser instalados manualmente e baixados em http://www.arduined.eu/ch340g-converter-windows-7-driver-download/ , caso utilize um SO windows 7 no computador

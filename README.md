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

	Para realizar a mudança na programação da impressora, foi necessario acessar a página Github de seu criador: 	https://github.com/lar-ect/impressoras-3d onde é possivel encontrar o repositorio completo de tudo sobre impressão 3D bem completo, inclusive um aprofundamento sobre a técnica de auto nivelamento da mesa de impressão em formato tutorial;
	
	A alteração é feita no arquivo Marlin, aberto pela IDE do Arduino (arquivo em formato .ino), do conjunto controlador da impressora que pode ser acessado em https://drive.google.com/open?id=0B7yvZReRz0z6RjZpb1BrNDZRWXc
(Aqui está o arquivo completo de uso geral em qualquer impressora 3D, sendo necessario definir os parametros especificos da máquina a qual será controlada pelo código encontrado nesse compartilhado);
	As modificações necessarias para Dolores estão registradas no repositorio: https://github.com/orivaldosantana/impressoras-3d/blob/master/CONFDolores.md , mas ficou faltando informar qual o dispositivo (board) que seleciona a referencia dessa máquina, e isso só foi percebido no vídeo https://www.youtube.com/watch?v=cpyZGah5Ct4, indicado pelo professor para servir de auxilio no procedimento de atualização do firmware, já que Dolores não respondia mais aos comandos do Pronterface após o upload do programa com as alterações que indica o repositorio.
	A alteração é feita na aba configuration.h
	Como medida de garantia e segurança, tinhamos um firmware de Dolores de sua ultima atualização antes de trocar o bico e a estrutura original do extrusor: https://drive.google.com/drive/folders/0B7yvZReRz0z6Ym5QbVUzcHdIQVE
	Foi observado também um problema no momento de conectar a impressora pelo Pronterface, onde após várias tentativas o próprio programa apontou uma falha na taxa de tranferência de dados (boundrate)

<p align="center">
  <a href="https://onsac.com/">
    <img src="https://github.com/onsac/AIO-Integrador/blob/master/Telas-Configura%C3%A7%C3%A3o/ONSAC%20-%20LOGO.png" >
  </a>
</p>

<h3 align="center">AIO-QUOTE</h3>

<p align="center">
  Projeto Integração ME + SIENGE
  <br>
  <a href="https://onsac.com/"><strong>Conheça mais sobre nosso serviço »</strong></a>
  </p>
  

## Topologia da Solução


<p align="center">
     <img src="https://github.com/onsac/aio-quote/blob/main/Topologia%20de%20Solu%C3%A7%C3%A3o%20%20-%20%20Integra%C3%A7%C3%A3o%20Parceiro%20de%20Compras.jpeg" >
</p>


## APIs – Mercado Eletrônico

Integração 1 Envio da Requisição (Criação /Alteração /Cancelamento) do ERP ao ME (Outbound) 
URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemRequisicao 

Integração 2 Envio de Pré -Pedido (Criação/Alteração) do ME ao ERP (Inbound) 
URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=getMessagePrePedido 

Integração 2.1 Retorno do Status de Erro/Inconsistência do ERP ao ME (Outbound) 
URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemStatusPrePedido 

Integração 2.2 Retorno do Pedido aprovado do ERP ao ME (Outbound) 
URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemStatusPrePedido 

Integração 3 Envio de Cancelamento de Pedido do ME ao ERP (Inbound) 
URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=getMessagePedido 

Integração 3.1 Retorno do Status do Pedido de Erro/Inconsistência do ERP ao ME (Outbound) 
URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=getMessageStatusPedido 

Integração 4 Envio de Recebimento Físico do ERP ao ME (Outbound) 
URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemEntrega 

Integração 5 Envio do Contrato (Criação/Alteração) do ME ao ERP (Inbound) 
URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemContratoWF 

Integração 5.1 Retorno do Status do Contrato de Erro/Inconsistência do ERP ao ME (Outbound) 
URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=getMessageStatusContrato 

Integração 6.2 Retorno do Contrato aprovado do ERP ao ME (Outbound) 
URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=getMessageStatusContrato 

Integração 7 Envio de Contas a Pagar do ERP ao ME (Outbound) 
URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemContaAPagar 

Integração 8 Envio de Contas Pagas do ERP ao ME (Outbound) 
URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemContasPagasList 

Integração 9 Carga de Fornecedores (Criação/Alteração/Bloqueio) do ERP ao ME (Outbound) 
URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemFornecedor 

Integração 10 Carga de Produtos (Criação/Alteração/Bloqueio) do ERP ao ME (Outbound) 
URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemProduto 

Integração 11 Carga de Objeto de Custo (Criação/Alteração/Bloqueio) do ERP ao ME (Outbound) 
URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemCentro_Custo

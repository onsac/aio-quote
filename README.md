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

* **Integração 1** Envio da Requisição (Criação /Alteração /Cancelamento) do ERP ao ME (Outbound)
  ```sh
  URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemRequisicao 
  ```

* **Integração 2** Envio de Pré -Pedido (Criação/Alteração) do ME ao ERP (Inbound) 
  ```sh
  URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=getMessagePrePedido 
  ``` 
  * **Integração 2.1** Retorno do Status de Erro/Inconsistência do ERP ao ME (Outbound)
  ```sh 
  URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemStatusPrePedido 
  ```
  * **Integração 2.2** Retorno do Pedido aprovado do ERP ao ME (Outbound)
  ```sh 
  URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemStatusPrePedido 
  ```
  
* **Integração 3** Envio de Cancelamento de Pedido do ME ao ERP (Inbound)
  ```sh
  URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=getMessagePedido 
  ```
  * **Integração 3.1** Retorno do Status do Pedido de Erro/Inconsistência do ERP ao ME (Outbound)
  ```sh 
  URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=getMessageStatusPedido 
  ```
* **Integração 4** Envio de Recebimento Físico do ERP ao ME (Outbound)
  ```sh 
  URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemEntrega 
  ```
* **Integração 5** Envio do Contrato (Criação/Alteração) do ME ao ERP (Inbound)
  ```sh 
  URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemContratoWF 
  ```
  * **Integração 5.1** Retorno do Status do Contrato de Erro/Inconsistência do ERP ao ME (Outbound)
  ```sh 
  URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=getMessageStatusContrato 
  ```
* **Integração 6** Retorno do Contrato aprovado do ERP ao ME (Outbound)
  ```sh 
  URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=getMessageStatusContrato 
  ```
* **Integração 7** Envio de Contas a Pagar do ERP ao ME (Outbound)
  ```sh 
  URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemContaAPagar 
  ```
* **Integração 8** Envio de Contas Pagas do ERP ao ME (Outbound)
  ```sh 
  URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemContasPagasList 
  ```
* **Integração 9** Carga de Fornecedores (Criação/Alteração/Bloqueio) do ERP ao ME (Outbound)
  ```sh 
  URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemFornecedor 
  ```
* **Integração 10** Carga de Produtos (Criação/Alteração/Bloqueio) do ERP ao ME (Outbound)
  ```sh 
  URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemProduto 
  ```
* **Integração 11** Carga de Objeto de Custo (Criação/Alteração/Bloqueio) do ERP ao ME (Outbound)
  ```sh 
  URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemCentro_Custo
  ```
## APIs – SIENGE

* **Integração 1** Busca solicitação de Compras (Outbound)
  ```sh 
  URL PROD: https://api.sienge.com.br/produtoeinovacao/public/api/v1/purchase-requests/{purchaseRequestId}
  ```
  * **Integração 1.1** Busca Item de Solicitação de Compra (Outbound)
  ```sh
  URL PROD: https://api.sienge.com.br/produtoeinovacao/public/api/v1/purchase-requests/all/items
  ```
* **Integração 2** Cria cotação de Preço (Inbound)
  ```sh
  URL PROD: https://api.sienge.com.br/produtoeinovacao/public/api/v1/purchase-quotations
  ```
* **Integração 3** Cria Negociação de Cotação de Preço com o Fornecedor (Inbound)
  ```sh 
  URL PROD: https://api.sienge.com.br/produtoeinovacao/public/api/v1/purchase-quotations/{puchaseQuotationId}/suppliers/{supplierId}/negotiations
  ```
  
## AIO-QUOTE – Contrato de APIs Origem e Destino

**SIENGE Webhook 1** Envia autorização de pedido de compra

PURCHASE_ORDER_AUTHORIZATION_CHANGED : Sempre que a autorização do pedido de compra mudar

```sh  
AIO-OPS API POST : http://<servidor aio>/api/cotação/purchaseOrder
```

```sh  
Payload  :  { "purchaseOrderId" : int, "authorized": boolean } 
```

**Integração 1** Busca solicitação de Compras 

```sh
API GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/purchase-requests/{purchaseRequestId}
```

```sh
{
  "id": 2104,
  "buildingId": 300,
  "departamentId": 5,
  "requesterUser": "USER",
  "requestDate": "2018-01-03",
  "notes": "Annotation",
  "status": "PENDING",
  "consitent": "CONSISTENT",
  "createdBy": "USER",
  "createdAt": "2018-03-11T14:20:00.000-03:00",
  "modifiedBy": "ANOTHERUSER",
  "modifiedAt": "2018-04-02T18:20:00.000-03:00"
}
```

**Integração 1.1** Busca Item de Solicitação de Compra

```sh
API GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/purchase-requests/all/items?purchaseRequestId={id}&buildingId={buildingId}
```

```sh
{
  "resultSetMetadata": { "count": 0, "offset": 0, "limit": 0  },
  "results": [
    {
      "productId": 1001,
      "detailId": 2,
      "trademarkId": 3,
      "quantity": 15,
      "unitySymbol": "un",
      "authorized": true,
      "disapproved": false,
      "competenceLevel": 0,
      "notes": "Descrição do item"
    }
  ],
  "links": [   {  "rel": "delivery-requirements",   "href": "http://../v1/purchase-requests/622/items/1/delivery-requirements"   }  ]
}
```

## Integração 1 Envio da Requisição (Criação /Alteração /Cancelamento) do ERP ao ME (Outbound) 

URL PROD: https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemRequisicao 
```sh
 <soap12:Body>
    <processarMensagemRequisicao xmlns="http://www.me.com.br/WebServices">
      <msgRequisicao>
        <IDINTEGRACAO>int</IDINTEGRACAO>
        <WORKFLOW>int</WORKFLOW>
        <IDREQUISITANTE>int</IDREQUISITANTE>
        <NOMEREQUISITANTE>string</NOMEREQUISITANTE>
        <CONTATOREQUISITANTE>string</CONTATOREQUISITANTE>
        <EMAILREQUISITANTE>string</EMAILREQUISITANTE>
        <TELEFONEREQUISITANTE>string</TELEFONEREQUISITANTE>
        <TAGREQUISITANTE>string</TAGREQUISITANTE>
        <STATUS>int</STATUS>
        <REQUISICAO>int</REQUISICAO>
        <REQUISICAOCLIENTE>string</REQUISICAOCLIENTE>
        <REQUISICAOORIGEM>string</REQUISICAOORIGEM>
        <LOCALENTREGACLIENTE>string</LOCALENTREGACLIENTE>
        <LocalEntrega>
          <IDINTEGRACAO>int</IDINTEGRACAO>
          <NOMELOCAL>string</NOMELOCAL>
          <CODIGO>string</CODIGO>
          <ENDERECO>string</ENDERECO>
          <NUMERO>string</NUMERO>
          <BAIRRO>string</BAIRRO>
          <COMPLEMENTO>string</COMPLEMENTO>
          <CIDADE>string</CIDADE>
          <ESTADO>string</ESTADO>
          <CEP>string</CEP>
          <CONTATO>string</CONTATO>
          <DDI>string</DDI>
          <TELEFONE>string</TELEFONE>
          <FAX>string</FAX>
          <PAIS>string</PAIS>
          <TIPO>int</TIPO>
          <CGC>string</CGC>
          <IE>string</IE>
          <SUFRAMA>string</SUFRAMA>
          <BLOQUEIAENVIOPEDIDO>string</BLOQUEIAENVIOPEDIDO>
          <EXCLUIDO>string</EXCLUIDO>
          <LOGINNAME>string</LOGINNAME>
          <NOMERECEBEDOR>string</NOMERECEBEDOR>
          <PERMITEPEDITEMNOUPLOADXMLDENFE>string</PERMITEPEDITEMNOUPLOADXMLDENFE>
          <LocaisBorgs>
            <LocaisBorg xsi:nil="true" />
            <LocaisBorg xsi:nil="true" />
          </LocaisBorgs>
        </LocalEntrega>
        <LOCALFATURAMENTOCLIENTE>string</LOCALFATURAMENTOCLIENTE>
        <LOCALCOBRANCACLIENTE>string</LOCALCOBRANCACLIENTE>
        <CENTROCUSTOSCLIENTE>string</CENTROCUSTOSCLIENTE>
        <TIPOCENTROCUSTO>string</TIPOCENTROCUSTO>
        <DATACOLOCACAO>dateTime</DATACOLOCACAO>
        <DATAENTREGA>dateTime</DATAENTREGA>
        <LOGIN>string</LOGIN>
        <OBSERVACAO>string</OBSERVACAO>
        <OBSRECUSA>string</OBSRECUSA>
        <OBSCLI>string</OBSCLI>
        <OBSSTATUSERP>string</OBSSTATUSERP>
        <REATIVO>string</REATIVO>
        <ALTERACAO>string</ALTERACAO>
        <DATAHORAALTERACAO>dateTime</DATAHORAALTERACAO>
        <CONTACONTABILCLIENTE>string</CONTACONTABILCLIENTE>
        <CATEGORIA>string</CATEGORIA>
        <CODIGOCATEGORIA>string</CODIGOCATEGORIA>
        <GRUPO_COMPRAS>string</GRUPO_COMPRAS>
        <CANCELADO>string</CANCELADO>
        <REQCONCLUIDO>string</REQCONCLUIDO>
        <REQLIBERADO>string</REQLIBERADO>
        <REQREJEITADO>string</REQREJEITADO>
        <DIAGRAMADEREDE>string</DIAGRAMADEREDE>
        <DATAHORA>dateTime</DATAHORA>
        <OI_INV>string</OI_INV>
        <TAG_STATUS>string</TAG_STATUS>
        <JUSTIFICATIVA>string</JUSTIFICATIVA>
        <DATAHORA_STATUS>dateTime</DATAHORA_STATUS>
        <DATACRIACAOERP>dateTime</DATACRIACAOERP>
        <DATALIBERACAOERP>dateTime</DATALIBERACAOERP>
        <EMAIL_GESTOR>string</EMAIL_GESTOR>
        <CONTRATOCLIENTE>string</CONTRATOCLIENTE>
        <GERARSO>string</GERARSO>
        <LocalEntregaBOrg>
          <Codigo>string</Codigo>
          <BOrgField>string</BOrgField>
          <BOrgCode>string</BOrgCode>
        </LocalEntregaBOrg>
        <CentroCustoBOrg>
          <Codigo>string</Codigo>
          <BOrgField>string</BOrgField>
          <BOrgCode>string</BOrgCode>
        </CentroCustoBOrg>
        <Objetos>
          <Propriedade>
            <Nome>string</Nome>
            <Valor>string</Valor>
          </Propriedade>
          <Propriedade>
            <Nome>string</Nome>
            <Valor>string</Valor>
          </Propriedade>
        </Objetos>
        <Atributos>
          <Atributo>
            <NomeAtributo>string</NomeAtributo>
            <DescricaoAtributo>string</DescricaoAtributo>
            <ValorAtributo>string</ValorAtributo>
          </Atributo>
          <Atributo>
            <NomeAtributo>string</NomeAtributo>
            <DescricaoAtributo>string</DescricaoAtributo>
            <ValorAtributo>string</ValorAtributo>
          </Atributo>
        </Atributos>
```        

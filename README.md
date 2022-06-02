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

## Integração 1 Envio da Requisição (Criação)

**URL PROD:** https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemRequisicao 
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
        <ItensRequisicao>
          <ItemRequisicao>
            <CANCELADO>string</CANCELADO>
            <QUANTIDADE>double</QUANTIDADE>
            <DESCRICAO>string</DESCRICAO>
            <COMPLEMENTO>string</COMPLEMENTO>
            <UNIDADE>string</UNIDADE>
            <UNIDADEALTERNATIVA>string</UNIDADEALTERNATIVA>
            <FABRICANTES>string</FABRICANTES>
            <FABRICANTES_CODIGO>string</FABRICANTES_CODIGO>
            <FABRICANTES_HOMOLOGADO>string</FABRICANTES_HOMOLOGADO>
            <CODIGO_GRUPO>string</CODIGO_GRUPO>
            <GRUPO_PRODUTO>string</GRUPO_PRODUTO>
            <PRAZOESTIMADO>int</PRAZOESTIMADO>
            <PRECOESTIMADO>double</PRECOESTIMADO>
            <REATIVO>string</REATIVO>
            <ALTERACAO>string</ALTERACAO>
            <DATAHORAALTERACAO>dateTime</DATAHORAALTERACAO>
            <NUMEROITEM>int</NUMEROITEM>
            <GENERICO>string</GENERICO>
            <MOEDA>string</MOEDA>
            <APLICACAO_MATERIAL>string</APLICACAO_MATERIAL>
            <FUP>int</FUP>
            <CODIGO_PRODUTO>string</CODIGO_PRODUTO>
            <CODIGOPRODUTOCLIENTE>string</CODIGOPRODUTOCLIENTE>
            <NBM>string</NBM>
            <STATUS>int</STATUS>
            <COTACAOCONTRATO>int</COTACAOCONTRATO>
            <IDENTIFICCONTRATO>string</IDENTIFICCONTRATO>
            <NUMEROITEMCONTRATO>int</NUMEROITEMCONTRATO>
            <IMOBILIZADO>int</IMOBILIZADO>
            <CATEGORIAMATERIAL>string</CATEGORIAMATERIAL>
            <CONTRATOCLIENTE>string</CONTRATOCLIENTE>
            <ITEMCONTRATO>int</ITEMCONTRATO>
            <UTILIZACAO_MATERIAL>string</UTILIZACAO_MATERIAL>
            <CONTARAZAO>string</CONTARAZAO>
            <IDENTIFIC_COT>string</IDENTIFIC_COT>
            <OBSCLI>string</OBSCLI>
            <CENTROCUSTOCLIENTE>string</CENTROCUSTOCLIENTE>
            <PEDIDOCLIENTE>string</PEDIDOCLIENTE>
            <NUMEROITEMPEDIDO>int</NUMEROITEMPEDIDO>
            <CATEGORIACONTABIL>string</CATEGORIACONTABIL>
            <CONTACONTABILCLIENTE>string</CONTACONTABILCLIENTE>
            <GRUPO_COMPRAS>string</GRUPO_COMPRAS>
            <PEP>string</PEP>
            <ORIGEMMATERIAL>int</ORIGEMMATERIAL>
            <CODIGO_GRUPO_PAI>string</CODIGO_GRUPO_PAI>
            <GRUPO_PRODUTO_PAI>string</GRUPO_PRODUTO_PAI>
            <CODIGO_GRUPO_PAI_2>string</CODIGO_GRUPO_PAI_2>
            <GRUPO_PRODUTO_PAI_2>string</GRUPO_PRODUTO_PAI_2>
            <PRODUTOBORGCODE>string</PRODUTOBORGCODE>
            <PRODUTOBORGFIELD>string</PRODUTOBORGFIELD>
            <CONTRATOSEL>int</CONTRATOSEL>
            <CONTRATOCLIENTESEL>string</CONTRATOCLIENTESEL>
            <ITEMCONTRATOSEL>int</ITEMCONTRATOSEL>
            <LocalEntregaItem>string</LocalEntregaItem>
            <LocalEntrega xsi:nil="true" />
            <LOCALENTREGACLIENTE>string</LOCALENTREGACLIENTE>
            <DATACOLOCACAO>dateTime</DATACOLOCACAO>
            <FORNECEDORCLIENTE>string</FORNECEDORCLIENTE>
            <DATAESPERADA>dateTime</DATAESPERADA>
            <LocalEntregaBOrg xsi:nil="true" />
            <CentroCustoBOrg xsi:nil="true" />
            <CodigoProdutoBOrg xsi:nil="true" />
            <TipoExportacao xsi:nil="true" />
            <Objetos xsi:nil="true" />
            <Atributos xsi:nil="true" />
            <RemocaoSubItens xsi:nil="true" />
            <CancelarItens xsi:nil="true" />
            <SubItens xsi:nil="true" />
            <Anexos xsi:nil="true" />
            <Entregas xsi:nil="true" />
            <RateioCC xsi:nil="true" />
            <RateioOI xsi:nil="true" />
            <ObjetosCusto xsi:nil="true" />
            <BOrgs xsi:nil="true" />
            <ProdutosBorgs xsi:nil="true" />
            <SERVICO>string</SERVICO>
            <CODIGOAF>string</CODIGOAF>
            <CODIGOFORNECEDORPARCEIRO>string</CODIGOFORNECEDORPARCEIRO>
            <GruposItem xsi:nil="true" />
            <TIPODOC>string</TIPODOC>
            <CODIGOIVA>string</CODIGOIVA>
            <IMPOSTOIVA>double</IMPOSTOIVA>
            <NAOGERAPREPEDIDOAUTOMATICO>string</NAOGERAPREPEDIDOAUTOMATICO>
            <PRIORIDADECOMPRA>int</PRIORIDADECOMPRA>
            <SOLICITACANCELAMENTO>string</SOLICITACANCELAMENTO>
            <DRAWBACK>string</DRAWBACK>
            <CATALOGTRADUCAO xsi:nil="true" />
            <PRODUTO>int</PRODUTO>
            <LOCALFATURAMENTOCLIENTE>string</LOCALFATURAMENTOCLIENTE>
            <LinkPersonalizado xsi:nil="true" />
          </ItemRequisicao>
          <ItemRequisicao>
            <CANCELADO>string</CANCELADO>
            <QUANTIDADE>double</QUANTIDADE>
            <DESCRICAO>string</DESCRICAO>
            <COMPLEMENTO>string</COMPLEMENTO>
            <UNIDADE>string</UNIDADE>
            <UNIDADEALTERNATIVA>string</UNIDADEALTERNATIVA>
            <FABRICANTES>string</FABRICANTES>
            <FABRICANTES_CODIGO>string</FABRICANTES_CODIGO>
            <FABRICANTES_HOMOLOGADO>string</FABRICANTES_HOMOLOGADO>
            <CODIGO_GRUPO>string</CODIGO_GRUPO>
            <GRUPO_PRODUTO>string</GRUPO_PRODUTO>
            <PRAZOESTIMADO>int</PRAZOESTIMADO>
            <PRECOESTIMADO>double</PRECOESTIMADO>
            <REATIVO>string</REATIVO>
            <ALTERACAO>string</ALTERACAO>
            <DATAHORAALTERACAO>dateTime</DATAHORAALTERACAO>
            <NUMEROITEM>int</NUMEROITEM>
            <GENERICO>string</GENERICO>
            <MOEDA>string</MOEDA>
            <APLICACAO_MATERIAL>string</APLICACAO_MATERIAL>
            <FUP>int</FUP>
            <CODIGO_PRODUTO>string</CODIGO_PRODUTO>
            <CODIGOPRODUTOCLIENTE>string</CODIGOPRODUTOCLIENTE>
            <NBM>string</NBM>
            <STATUS>int</STATUS>
            <COTACAOCONTRATO>int</COTACAOCONTRATO>
            <IDENTIFICCONTRATO>string</IDENTIFICCONTRATO>
            <NUMEROITEMCONTRATO>int</NUMEROITEMCONTRATO>
            <IMOBILIZADO>int</IMOBILIZADO>
            <CATEGORIAMATERIAL>string</CATEGORIAMATERIAL>
            <CONTRATOCLIENTE>string</CONTRATOCLIENTE>
            <ITEMCONTRATO>int</ITEMCONTRATO>
            <UTILIZACAO_MATERIAL>string</UTILIZACAO_MATERIAL>
            <CONTARAZAO>string</CONTARAZAO>
            <IDENTIFIC_COT>string</IDENTIFIC_COT>
            <OBSCLI>string</OBSCLI>
            <CENTROCUSTOCLIENTE>string</CENTROCUSTOCLIENTE>
            <PEDIDOCLIENTE>string</PEDIDOCLIENTE>
            <NUMEROITEMPEDIDO>int</NUMEROITEMPEDIDO>
            <CATEGORIACONTABIL>string</CATEGORIACONTABIL>
            <CONTACONTABILCLIENTE>string</CONTACONTABILCLIENTE>
            <GRUPO_COMPRAS>string</GRUPO_COMPRAS>
            <PEP>string</PEP>
            <ORIGEMMATERIAL>int</ORIGEMMATERIAL>
            <CODIGO_GRUPO_PAI>string</CODIGO_GRUPO_PAI>
            <GRUPO_PRODUTO_PAI>string</GRUPO_PRODUTO_PAI>
            <CODIGO_GRUPO_PAI_2>string</CODIGO_GRUPO_PAI_2>
            <GRUPO_PRODUTO_PAI_2>string</GRUPO_PRODUTO_PAI_2>
            <PRODUTOBORGCODE>string</PRODUTOBORGCODE>
            <PRODUTOBORGFIELD>string</PRODUTOBORGFIELD>
            <CONTRATOSEL>int</CONTRATOSEL>
            <CONTRATOCLIENTESEL>string</CONTRATOCLIENTESEL>
            <ITEMCONTRATOSEL>int</ITEMCONTRATOSEL>
            <LocalEntregaItem>string</LocalEntregaItem>
            <LocalEntrega xsi:nil="true" />
            <LOCALENTREGACLIENTE>string</LOCALENTREGACLIENTE>
            <DATACOLOCACAO>dateTime</DATACOLOCACAO>
            <FORNECEDORCLIENTE>string</FORNECEDORCLIENTE>
            <DATAESPERADA>dateTime</DATAESPERADA>
            <LocalEntregaBOrg xsi:nil="true" />
            <CentroCustoBOrg xsi:nil="true" />
            <CodigoProdutoBOrg xsi:nil="true" />
            <TipoExportacao xsi:nil="true" />
            <Objetos xsi:nil="true" />
            <Atributos xsi:nil="true" />
            <RemocaoSubItens xsi:nil="true" />
            <CancelarItens xsi:nil="true" />
            <SubItens xsi:nil="true" />
            <Anexos xsi:nil="true" />
            <Entregas xsi:nil="true" />
            <RateioCC xsi:nil="true" />
            <RateioOI xsi:nil="true" />
            <ObjetosCusto xsi:nil="true" />
            <BOrgs xsi:nil="true" />
            <ProdutosBorgs xsi:nil="true" />
            <SERVICO>string</SERVICO>
            <CODIGOAF>string</CODIGOAF>
            <CODIGOFORNECEDORPARCEIRO>string</CODIGOFORNECEDORPARCEIRO>
            <GruposItem xsi:nil="true" />
            <TIPODOC>string</TIPODOC>
            <CODIGOIVA>string</CODIGOIVA>
            <IMPOSTOIVA>double</IMPOSTOIVA>
            <NAOGERAPREPEDIDOAUTOMATICO>string</NAOGERAPREPEDIDOAUTOMATICO>
            <PRIORIDADECOMPRA>int</PRIORIDADECOMPRA>
            <SOLICITACANCELAMENTO>string</SOLICITACANCELAMENTO>
            <DRAWBACK>string</DRAWBACK>
            <CATALOGTRADUCAO xsi:nil="true" />
            <PRODUTO>int</PRODUTO>
            <LOCALFATURAMENTOCLIENTE>string</LOCALFATURAMENTOCLIENTE>
            <LinkPersonalizado xsi:nil="true" />
          </ItemRequisicao>
        </ItensRequisicao>
        <BOrgs>
          <BOrg>
            <CodigoBOrg>string</CodigoBOrg>
            <DescricaoBOrg>string</DescricaoBOrg>
            <DescricaoVEnt>string</DescricaoVEnt>
            <CampoVEnt>string</CampoVEnt>
            <TipoEntidade>string</TipoEntidade>
            <BOrgID>int</BOrgID>
          </BOrg>
          <BOrg>
            <CodigoBOrg>string</CodigoBOrg>
            <DescricaoBOrg>string</DescricaoBOrg>
            <DescricaoVEnt>string</DescricaoVEnt>
            <CampoVEnt>string</CampoVEnt>
            <TipoEntidade>string</TipoEntidade>
            <BOrgID>int</BOrgID>
          </BOrg>
        </BOrgs>
        <REQUISICAOSAP>string</REQUISICAOSAP>
        <EMERGENCIAL>string</EMERGENCIAL>
        <CAMPOREQUISICAOINTEGRADA>string</CAMPOREQUISICAOINTEGRADA>
        <TIPODOCUMENTO>string</TIPODOCUMENTO>
        <NOMEFICHEIROSIVA>string</NOMEFICHEIROSIVA>
        <ORDEM>string</ORDEM>
        <PEP>string</PEP>
        <TITULO>string</TITULO>
        <INVISIVEL>string</INVISIVEL>
        <CONDPAG>string</CONDPAG>
        <IDFORNECEDOR>int</IDFORNECEDOR>
        <MOEDA>string</MOEDA>
        <AprovadoresRequisicao>
          <WORKFLOW>int</WORKFLOW>
          <IDFORNECEDOR>int</IDFORNECEDOR>
          <AprovadorRequisicao>
            <AprovadorRequisicao xsi:nil="true" />
            <AprovadorRequisicao xsi:nil="true" />
          </AprovadorRequisicao>
        </AprovadoresRequisicao>
        <LinkPersonalizado>
          <LinkPersonalizado>
            <URL>string</URL>
            <TITULO>string</TITULO>
            <TIPO>string</TIPO>
          </LinkPersonalizado>
          <LinkPersonalizado>
            <URL>string</URL>
            <TITULO>string</TITULO>
            <TIPO>string</TIPO>
          </LinkPersonalizado>
        </LinkPersonalizado>
      </msgRequisicao>
    </processarMensagemRequisicao>
  </soap12:Body>
```

## Contrato de Request - PRESTES - Criação de COtação

Este Contrato de Request, baseado na disponibilidade de atributos apresentado no topico acima, define quais são os atributos que serão enviados, os tipo de valores, e os domínios caso exista, os campos requeridos pelo ME para atender a está requisição também devem ser definodos neste contrato:

```sh
  <soap12:Body>
    <processarMensagemRequisicao xmlns="http://www.me.com.br/WebServices">
      <msgRequisicao>
        ...
        <LocalEntrega>
          ...
        <LocalEntregaBOrg>
          ...
        <CentroCustoBOrg>
          ...
        <Objetos>
          ...
        <Atributos>
          ...
        <ItensRequisicao>
          ...
        <BOrgs>
          ...
        <AprovadoresRequisicao>
          ...
        <LinkPersonalizado>
          ...
      </msgRequisicao>
    </processarMensagemRequisicao>
  </soap12:Body>  
```


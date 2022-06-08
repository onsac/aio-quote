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

> **Integração 1** Busca autorização de Solicitação de Compra
```sh 
  GET : https://api.sienge.com.br/produtoeinovacao/public/api/v1/purchase-requests/all/items?startDate=2022-03-01&endDate=2022-03-30&authorized=true
```
```sh
{
   "results": [
        {
            "purchaseRequestId": 842,
            "itemNumber": 1,
            "productId": 1010,
            "productDescription": "Prego",
            "detailId": null,
            "detailDescription": "",
            "trademarkId": null,
            "trademarkDescription": "",
            "quantity": 10.0,
            "unitySymbol": "kg",
            "notes": "",
            "authorized": true,
            "disapproved": false,
            "competenceLevel": null,
            "tenantUrl": "https://api.sienge.com.br/produtoeinovacao/public/api",
            "links": [
                {
                    "rel": "delivery-requirements",
                    "href": "https://api.sienge.com.br/produtoeinovacao/public/api/v1/purchase-requests/842/items/1/delivery-requirements"
                }
            ]
        },
    "resultSetMetadata": {
        "count": 5,
        "offset": 0,
        "limit": 100
    },
    "links": [
        {
            "rel": "self",
            "href": "https://api.sienge.com.br/produtoeinovacao/public/api/v1/purchase-requests/all/items?startDate=2022-03-01&endDate=2022-03-30&authorized=true&limit=100"
        }
    ]
}
```

> **Integração 1.1** : Busca solicitação de Compras 

```diff
+ API GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/purchase-requests/{purchaseRequestId}
```

```sh
{
    "id": 842,
    "buildingId": 4,
    "departamentId": null,
    "requesterUser": "CONAZ",
    "requestDate": "2022-03-24",
    "notes": "",
    "status": "PENDING",
    "consistent": "CONSISTENT",
    "createdBy": "CONAZ",
    "createdAt": "2022-03-24T10:23:30.870-03:00",
    "modifiedBy": "CONAZ",
    "modifiedAt": "2022-03-24T10:25:00.373-03:00"
}
```

> **Integração 1.2** : Busca Item de Solicitação de Compra

```diff
+ API GET: https://api.sienge.com.br/produtoeinovacao/public/api/v1/purchase-requests/{purchaseRequestId}/items/{itemNumber}/delivery-requirements
```

```sh
{
    "results": [
        {
            "deliveryRequirementNumber": 1,
            "requirementDate": "2022-03-24",
            "requirementQuantity": 10.0,
            "attendedQuantity": 0.0,
            "openQuantity": true
        }
    ],
    "resultSetMetadata": {
        "count": 1,
        "offset": 0,
        "limit": 100
    },
    "links": [
        {
            "rel": "self",
            "href": "https://api.sienge.com.br/produtoeinovacao/public/api/v1/purchase-requests/842/items/1/delivery-requirements?limit=100"
        }
    ]
}
```

> **Integração 2** : Envio da Requisição (Criação)

```diff
+ **URL API ME POST** : https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemRequisicao 
```

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
> **Integração 3** : Envio de Pré -Pedido (Criado) do ME ao ERP (Inbound)

```diff
+ **URL API ME GET** : https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=getMessagePrePedido
```

```sh
<soap12:Body>
    <getMessagePrePedidoResponse xmlns="http://www.me.com.br/WebServices">
      <getMessagePrePedidoResult>
        <Token>string</Token>
        <Message>
          <PREPEDIDO>int</PREPEDIDO>
          <STATUS>int</STATUS>
          <CANCELADO>string</CANCELADO>
          <IDENTIFIC>string</IDENTIFIC>
          <IDFORNECEDOR>int</IDFORNECEDOR>
          <FORNECEDOR>int</FORNECEDOR>
          <RESUMO>string</RESUMO>
          <DATAHORALIMITE>dateTime</DATAHORALIMITE>
          <OBSCLI>string</OBSCLI>
          <ICMS>double</ICMS>
          <ICMS_INCLUSO>string</ICMS_INCLUSO>
          <FRETE>string</FRETE>
          <VALORFRETE>double</VALORFRETE>
          <COND_PAGTO>string</COND_PAGTO>
          <COND_ENTREGA>string</COND_ENTREGA>
          <DATAENTREGA>dateTime</DATAENTREGA>
          <VALIDADE>dateTime</VALIDADE>
          <LOGIN>string</LOGIN>
          <FORNECEDORCLIENTE>string</FORNECEDORCLIENTE>
          <FORNECEDORCLIENTEPRINCIPAL>string</FORNECEDORCLIENTEPRINCIPAL>
          <MOEDA>string</MOEDA>
          <TAXACONVERSAO>double</TAXACONVERSAO>
          <TAXACONVERSAOESTIMADA>double</TAXACONVERSAOESTIMADA>
          <PRAZOENTREGA>int</PRAZOENTREGA>
          <OBSRECUSA>string</OBSRECUSA>
          <COTACAO>int</COTACAO>
          <IDENTIFIC_COT>string</IDENTIFIC_COT>
          <CENTRO>string</CENTRO>
          <PROJETO>string</PROJETO>
          <EMPRESA>string</EMPRESA>
          <ORGANIZACAO_COMPRAS>string</ORGANIZACAO_COMPRAS>
          <BORG_CENTRO>string</BORG_CENTRO>
          <GRUPO_COMPRAS>string</GRUPO_COMPRAS>
          <ALTERACAO>string</ALTERACAO>
          <CODCOMPRFUP>string</CODCOMPRFUP>
          <CNPJTRANSPORTADORA>string</CNPJTRANSPORTADORA>
          <Atributos>
            <Atributo xsi:nil="true" />
            <Atributo xsi:nil="true" />
          </Atributos>
          <DATAHORAGERACAO>dateTime</DATAHORAGERACAO>
          <LOCALENTREGACLIENTE>string</LOCALENTREGACLIENTE>
          <LOCALCOBRANCACLIENTE>string</LOCALCOBRANCACLIENTE>
          <LOCALREALCOBRANCA>string</LOCALREALCOBRANCA>
          <LOCALFATURAMENTOCLIENTE>string</LOCALFATURAMENTOCLIENTE>
          <TAG>string</TAG>
          <CNPJFORNECEDOR>string</CNPJFORNECEDOR>
          <CONTRATO>int</CONTRATO>
          <CONTRATOCLIENTE>string</CONTRATOCLIENTE>
          <AREAGESTORA>string</AREAGESTORA>
          <TIPOPEDIDOCAT>string</TIPOPEDIDOCAT>
          <MULTIPLASDATAS>string</MULTIPLASDATAS>
          <CODTRANSPORTADORA>string</CODTRANSPORTADORA>
          <IMPOSTOIVAINCLUSO>string</IMPOSTOIVAINCLUSO>
          <IMPOSTOIVA>double</IMPOSTOIVA>
          <JUSTIFICATIVA>string</JUSTIFICATIVA>
          <CATEGORIA>string</CATEGORIA>
          <CENTROCUSTOCLIENTE>string</CENTROCUSTOCLIENTE>
          <FORNECEDORFRETE>string</FORNECEDORFRETE>
          <FORNECEDORPARCEIRO>string</FORNECEDORPARCEIRO>
          <FORNECEDORCLIENTEPARCEIRO>string</FORNECEDORCLIENTEPARCEIRO>
          <FORNECEDORCLIENTEPARCEIROPRINCIPAL>string</FORNECEDORCLIENTEPARCEIROPRINCIPAL>
          <REMESSAFUTURA>string</REMESSAFUTURA>
          <PEDIDOFRETECLIENTE>string</PEDIDOFRETECLIENTE>
          <LIMITEFATURAMENTO>double</LIMITEFATURAMENTO>
          <FORNECEDORSUBSTITUTO>string</FORNECEDORSUBSTITUTO>
          <BOrgs>
            <BOrg xsi:nil="true" />
            <BOrg xsi:nil="true" />
          </BOrgs>
          <Itens>
            <ItemPrePedido xsi:nil="true" />
            <ItemPrePedido xsi:nil="true" />
          </Itens>
          <RequisicoesPrePedido>
            <RequisicaoPrePedido xsi:nil="true" />
            <RequisicaoPrePedido xsi:nil="true" />
          </RequisicoesPrePedido>
          <CotacoesPrePedido>
            <CotacaoPrePedido xsi:nil="true" />
            <CotacaoPrePedido xsi:nil="true" />
          </CotacoesPrePedido>
          <MsgFornecedor>
            <IDINTEGRACAO>int</IDINTEGRACAO>
            <ContatosBorg xsi:nil="true" />
            <IDFORNECEDOR>int</IDFORNECEDOR>
            <FORNECEDORCLIENTE>string</FORNECEDORCLIENTE>
            <NOME>string</NOME>
            <RAZAO>string</RAZAO>
            <CONTATO>string</CONTATO>
            <ENDERECO>string</ENDERECO>
            <ENDERECONUMERO>string</ENDERECONUMERO>
            <ENDERECOCOMPLEMENTO>string</ENDERECOCOMPLEMENTO>
            <CIDADE>string</CIDADE>
            <REGIAO>string</REGIAO>
            <ESTADO>string</ESTADO>
            <PAIS>string</PAIS>
            <CEP>string</CEP>
            <CELULAR>string</CELULAR>
            <CONTATO2>string</CONTATO2>
            <EMAIL2>string</EMAIL2>
            <BAIRRO>string</BAIRRO>
            <TELEFONE>string</TELEFONE>
            <FAX>string</FAX>
            <URL>string</URL>
            <EMAIL>string</EMAIL>
            <CPF>string</CPF>
            <CUIT>string</CUIT>
            <CNPJ>string</CNPJ>
            <RUT>string</RUT>
            <CCM>string</CCM>
            <IE>string</IE>
            <ATIVIDADE>string</ATIVIDADE>
            <BANCO>string</BANCO>
            <AGENCIA>string</AGENCIA>
            <CONTA>string</CONTA>
            <PRACA>string</PRACA>
            <INTERNACIONAL>int</INTERNACIONAL>
            <GRUPO_FORNECEDOR>string</GRUPO_FORNECEDOR>
            <DDI>string</DDI>
            <BLOQUEADO>string</BLOQUEADO>
            <POVOADO>string</POVOADO>
            <FORNECEDOR>int</FORNECEDOR>
            <OBSERVACAO>string</OBSERVACAO>
            <NOMECORRENTISTA>string</NOMECORRENTISTA>
            <DOCCORRENTISTA>string</DOCCORRENTISTA>
            <BONIFICACAO>double</BONIFICACAO>
            <CONDICAOPAGAMENTO>string</CONDICAOPAGAMENTO>
            <TIPOALTERACAO>string</TIPOALTERACAO>
            <LOGINRESPONSAVEL>string</LOGINRESPONSAVEL>
            <UtilizaContasPagasPagar>string</UtilizaContasPagasPagar>
            <BOrgItens xsi:nil="true" />
            <ContasCorrente xsi:nil="true" />
            <GruposProduto xsi:nil="true" />
            <FornecedorEstrategico>string</FornecedorEstrategico>
            <FornecedorContas xsi:nil="true" />
            <IDF>double</IDF>
            <Atributos xsi:nil="true" />
            <MOEDA>string</MOEDA>
            <EMAILSADICIONAIS>string</EMAILSADICIONAIS>
            <EmailsPorProcesso xsi:nil="true" />
            <MATERIALTREINAMENTO>string</MATERIALTREINAMENTO>
            <TIPODOCUMENTO>string</TIPODOCUMENTO>
            <NUMERODOCUMENTO>string</NUMERODOCUMENTO>
            <EMAILCOBRANCA>string</EMAILCOBRANCA>
            <ENDERECOCOBRANCA>string</ENDERECOCOBRANCA>
            <CONTATOCOBRANCA>string</CONTATOCOBRANCA>
            <STATUS_HOMOLOGACAO>string</STATUS_HOMOLOGACAO>
            <CEPCOBRANCA>string</CEPCOBRANCA>
            <MUNICIPIOCOBRANCA>string</MUNICIPIOCOBRANCA>
            <ESTADOCOBRANCA>string</ESTADOCOBRANCA>
            <PAISCOBRANCA>string</PAISCOBRANCA>
            <TIPOPAGAMENTO>string</TIPOPAGAMENTO>
            <NOTAMEDIA>string</NOTAMEDIA>
            <BOrgPgtoItens xsi:nil="true" />
            <LinkPersonalizado xsi:nil="true" />
            <BOrgLocalFaturamento xsi:nil="true" />
          </MsgFornecedor>
          <FormasPagamento>
            <FormaPagamentoPrePedido xsi:nil="true" />
            <FormaPagamentoPrePedido xsi:nil="true" />
          </FormasPagamento>
          <AprovadoresPrePedido>
            <WORKFLOW>int</WORKFLOW>
            <IDFORNECEDOR>int</IDFORNECEDOR>
            <AprovadorPrePedido xsi:nil="true" />
          </AprovadoresPrePedido>
          <LocaisEntregaPrePedido>
            <LocalEntregaPrePedido xsi:nil="true" />
          </LocaisEntregaPrePedido>
          <LocaisCobrancaPrePedido>
            <LocalCobrancaPrePedido xsi:nil="true" />
          </LocaisCobrancaPrePedido>
          <Propriedades>
            <Propriedade xsi:nil="true" />
            <Propriedade xsi:nil="true" />
          </Propriedades>
          <Objetos>
            <Propriedade xsi:nil="true" />
            <Propriedade xsi:nil="true" />
          </Objetos>
          <Textos>
            <TextoGenerico xsi:nil="true" />
            <TextoGenerico xsi:nil="true" />
          </Textos>
          <RelatorioNegociacao>
            <TIPOPROCESSO>string</TIPOPROCESSO>
            <RESPONSAVEL>string</RESPONSAVEL>
            <CATEGORIARELATORIO>string</CATEGORIARELATORIO>
            <OBJETO>string</OBJETO>
            <OBSERVACAO>string</OBSERVACAO>
            <OBSERVACAOAPROVADOR>string</OBSERVACAOAPROVADOR>
            <OBSERVACAOGERAL>string</OBSERVACAOGERAL>
            <DATAINICIALPRAZO>dateTime</DATAINICIALPRAZO>
            <DATAFINALPRAZO>dateTime</DATAFINALPRAZO>
            <CONTRATOCLIENTE>string</CONTRATOCLIENTE>
            <VALORTOTAL>double</VALORTOTAL>
          </RelatorioNegociacao>
          <CustoAdicional>
            <CustoAdicionalValor xsi:nil="true" />
            <CustoAdicionalValor xsi:nil="true" />
          </CustoAdicional>
          <RequisicaoID>int</RequisicaoID>
          <CAMPOREQUISICAOINTEGRADAPREPEDIDO>string</CAMPOREQUISICAOINTEGRADAPREPEDIDO>
          <TIPODOCUMENTO>string</TIPODOCUMENTO>
          <NOMEFICHEIROSIVA>string</NOMEFICHEIROSIVA>
          <OPERACAO_COMERCIAL>string</OPERACAO_COMERCIAL>
          <TIPOFORNECEDORPARCEIRO>string</TIPOFORNECEDORPARCEIRO>
          <INVISIVEL>string</INVISIVEL>
          <ELEMENTOPEP>string</ELEMENTOPEP>
          <OBSERVACAOAPROVADOR>string</OBSERVACAOAPROVADOR>
          <ColetaPreco>
            <COTACAO>int</COTACAO>
            <IDCOMPRADOR>int</IDCOMPRADOR>
            <STATUSCOTACAO>int</STATUSCOTACAO>
            <DATALEITURA>dateTime</DATALEITURA>
            <COTACAOCLIENTE>string</COTACAOCLIENTE>
            <COTACAO_ORIGINAL>int</COTACAO_ORIGINAL>
            <GRUPO_COMPRAS>string</GRUPO_COMPRAS>
            <RESUMO>string</RESUMO>
            <CATEGORIA>string</CATEGORIA>
            <DATACOLOCACAO>dateTime</DATACOLOCACAO>
            <TAGCOMPRADOR>string</TAGCOMPRADOR>
            <IDREQUISITANTE>int</IDREQUISITANTE>
            <CODCLICOMPRADOR>string</CODCLICOMPRADOR>
            <DATALIMITE>dateTime</DATALIMITE>
            <PREPEDIDO>int</PREPEDIDO>
            <BOrgs xsi:nil="true" />
            <FornecedoresColeta xsi:nil="true" />
            <RequisicoesColeta xsi:nil="true" />
            <Propriedades xsi:nil="true" />
            <Objetos xsi:nil="true" />
          </ColetaPreco>
          <OUTRASDESPESAS>double</OUTRASDESPESAS>
        </Message>
      </getMessagePrePedidoResult>
    </getMessagePrePedidoResponse>
  </soap12:Body>
```
> **Integração 3**    : Envio de Fornecedor

```diff
+ **URL API ME POST** : https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemFornecedor
```

```sh
<soap12:Body>
    <processarMensagemFornecedor xmlns="http://www.me.com.br/WebServices">
      <msgFornecedor>
        <IDINTEGRACAO>int</IDINTEGRACAO>
        <ContatosBorg>
          <ContatosBorg>
            <CONTATO>string</CONTATO>
            <EMAIL>string</EMAIL>
            <TELEFONE>string</TELEFONE>
            <CAMPOVENT>string</CAMPOVENT>
            <CODIGOBORG>string</CODIGOBORG>
            <EXCLUSAO>string</EXCLUSAO>
          </ContatosBorg>
          <ContatosBorg>
            <CONTATO>string</CONTATO>
            <EMAIL>string</EMAIL>
            <TELEFONE>string</TELEFONE>
            <CAMPOVENT>string</CAMPOVENT>
            <CODIGOBORG>string</CODIGOBORG>
            <EXCLUSAO>string</EXCLUSAO>
          </ContatosBorg>
        </ContatosBorg>
        <IDFORNECEDOR>int</IDFORNECEDOR>
        <FORNECEDORCLIENTE>string</FORNECEDORCLIENTE>
        <NOME>string</NOME>
        <RAZAO>string</RAZAO>
        <CONTATO>string</CONTATO>
        <ENDERECO>string</ENDERECO>
        <ENDERECONUMERO>string</ENDERECONUMERO>
        <ENDERECOCOMPLEMENTO>string</ENDERECOCOMPLEMENTO>
        <CIDADE>string</CIDADE>
        <REGIAO>string</REGIAO>
        <ESTADO>string</ESTADO>
        <PAIS>string</PAIS>
        <CEP>string</CEP>
        <CELULAR>string</CELULAR>
        <CONTATO2>string</CONTATO2>
        <EMAIL2>string</EMAIL2>
        <BAIRRO>string</BAIRRO>
        <TELEFONE>string</TELEFONE>
        <FAX>string</FAX>
        <URL>string</URL>
        <EMAIL>string</EMAIL>
        <CPF>string</CPF>
        <CUIT>string</CUIT>
        <CNPJ>string</CNPJ>
        <RUT>string</RUT>
        <CCM>string</CCM>
        <IE>string</IE>
        <ATIVIDADE>string</ATIVIDADE>
        <BANCO>string</BANCO>
        <AGENCIA>string</AGENCIA>
        <CONTA>string</CONTA>
        <PRACA>string</PRACA>
        <INTERNACIONAL>int</INTERNACIONAL>
        <GRUPO_FORNECEDOR>string</GRUPO_FORNECEDOR>
        <DDI>string</DDI>
        <BLOQUEADO>string</BLOQUEADO>
        <POVOADO>string</POVOADO>
        <FORNECEDOR>int</FORNECEDOR>
        <OBSERVACAO>string</OBSERVACAO>
        <NOMECORRENTISTA>string</NOMECORRENTISTA>
        <DOCCORRENTISTA>string</DOCCORRENTISTA>
        <BONIFICACAO>double</BONIFICACAO>
        <CONDICAOPAGAMENTO>string</CONDICAOPAGAMENTO>
        <TIPOALTERACAO>string</TIPOALTERACAO>
        <LOGINRESPONSAVEL>string</LOGINRESPONSAVEL>
        <UtilizaContasPagasPagar>string</UtilizaContasPagasPagar>
        <BOrgItens>
          <FornecedorBOrg>
            <CodigoBOrg>string</CodigoBOrg>
            <CampoVEnt>string</CampoVEnt>
            <FORNECEDORCLIENTE>string</FORNECEDORCLIENTE>
            <GENERICO>string</GENERICO>
            <BLOQUEADO>string</BLOQUEADO>
            <REPLICARBORGS>string</REPLICARBORGS>
            <CODIGOCONDICAOPAGAMENTPADRAO>string</CODIGOCONDICAOPAGAMENTPADRAO>
            <NUMEROCONDICAOPAGAMENTPADRAO>int</NUMEROCONDICAOPAGAMENTPADRAO>
            <ALTERARCONDICAOPAGAMENTPADRAO>string</ALTERARCONDICAOPAGAMENTPADRAO>
          </FornecedorBOrg>
          <FornecedorBOrg>
            <CodigoBOrg>string</CodigoBOrg>
            <CampoVEnt>string</CampoVEnt>
            <FORNECEDORCLIENTE>string</FORNECEDORCLIENTE>
            <GENERICO>string</GENERICO>
            <BLOQUEADO>string</BLOQUEADO>
            <REPLICARBORGS>string</REPLICARBORGS>
            <CODIGOCONDICAOPAGAMENTPADRAO>string</CODIGOCONDICAOPAGAMENTPADRAO>
            <NUMEROCONDICAOPAGAMENTPADRAO>int</NUMEROCONDICAOPAGAMENTPADRAO>
            <ALTERARCONDICAOPAGAMENTPADRAO>string</ALTERARCONDICAOPAGAMENTPADRAO>
          </FornecedorBOrg>
        </BOrgItens>
        <ContasCorrente>
          <FornecedorContaCorrente>
            <CodigoConta>string</CodigoConta>
            <Principal>string</Principal>
          </FornecedorContaCorrente>
          <FornecedorContaCorrente>
            <CodigoConta>string</CodigoConta>
            <Principal>string</Principal>
          </FornecedorContaCorrente>
        </ContasCorrente>
        <GruposProduto>
          <FornecedorGrupoProduto>
            <CodigoGrupo>string</CodigoGrupo>
            <DescricaoGrupo>string</DescricaoGrupo>
          </FornecedorGrupoProduto>
          <FornecedorGrupoProduto>
            <CodigoGrupo>string</CodigoGrupo>
            <DescricaoGrupo>string</DescricaoGrupo>
          </FornecedorGrupoProduto>
        </GruposProduto>
        <FornecedorEstrategico>string</FornecedorEstrategico>
        <FornecedorContas>
          <FornecedorContas>
            <Id>int</Id>
            <Fornecedor>int</Fornecedor>
            <Banco>string</Banco>
            <Agencia>string</Agencia>
            <Conta>string</Conta>
            <DigitoAgencia>string</DigitoAgencia>
            <DigitoConta>string</DigitoConta>
            <NomeCorrentista>string</NomeCorrentista>
            <Ativo>string</Ativo>
          </FornecedorContas>
          <FornecedorContas>
            <Id>int</Id>
            <Fornecedor>int</Fornecedor>
            <Banco>string</Banco>
            <Agencia>string</Agencia>
            <Conta>string</Conta>
            <DigitoAgencia>string</DigitoAgencia>
            <DigitoConta>string</DigitoConta>
            <NomeCorrentista>string</NomeCorrentista>
            <Ativo>string</Ativo>
          </FornecedorContas>
        </FornecedorContas>
        <IDF>double</IDF>
        <Atributos>
          <RespostaAtributoMeusFornecedores>
            <ID>int</ID>
            <Fornecedor>int</Fornecedor>
            <Nome>string</Nome>
            <Valor>string</Valor>
            <Descricao>string</Descricao>
          </RespostaAtributoMeusFornecedores>
          <RespostaAtributoMeusFornecedores>
            <ID>int</ID>
            <Fornecedor>int</Fornecedor>
            <Nome>string</Nome>
            <Valor>string</Valor>
            <Descricao>string</Descricao>
          </RespostaAtributoMeusFornecedores>
        </Atributos>
        <MOEDA>string</MOEDA>
        <EMAILSADICIONAIS>string</EMAILSADICIONAIS>
        <EmailsPorProcesso>
          <EmailProcesso>
            <Processo>string</Processo>
            <EMail>string</EMail>
          </EmailProcesso>
          <EmailProcesso>
            <Processo>string</Processo>
            <EMail>string</EMail>
          </EmailProcesso>
        </EmailsPorProcesso>
        <MATERIALTREINAMENTO>string</MATERIALTREINAMENTO>
        <TIPODOCUMENTO>string</TIPODOCUMENTO>
        <NUMERODOCUMENTO>string</NUMERODOCUMENTO>
        <EMAILCOBRANCA>string</EMAILCOBRANCA>
        <ENDERECOCOBRANCA>string</ENDERECOCOBRANCA>
        <CONTATOCOBRANCA>string</CONTATOCOBRANCA>
        <STATUS_HOMOLOGACAO>string</STATUS_HOMOLOGACAO>
        <CEPCOBRANCA>string</CEPCOBRANCA>
        <MUNICIPIOCOBRANCA>string</MUNICIPIOCOBRANCA>
        <ESTADOCOBRANCA>string</ESTADOCOBRANCA>
        <PAISCOBRANCA>string</PAISCOBRANCA>
        <TIPOPAGAMENTO>string</TIPOPAGAMENTO>
        <NOTAMEDIA>string</NOTAMEDIA>
        <BOrgPgtoItens>
          <BOrgPgtoItens>
            <CodigoBOrg>string</CodigoBOrg>
            <CampoVEnt>string</CampoVEnt>
            <FORNECEDORCLIENTE>string</FORNECEDORCLIENTE>
            <CONDICAOPAGAMENTO>string</CONDICAOPAGAMENTO>
            <BLOQUEADO>string</BLOQUEADO>
          </BOrgPgtoItens>
          <BOrgPgtoItens>
            <CodigoBOrg>string</CodigoBOrg>
            <CampoVEnt>string</CampoVEnt>
            <FORNECEDORCLIENTE>string</FORNECEDORCLIENTE>
            <CONDICAOPAGAMENTO>string</CONDICAOPAGAMENTO>
            <BLOQUEADO>string</BLOQUEADO>
          </BOrgPgtoItens>
        </BOrgPgtoItens>
        <LinkPersonalizado>
          <LinkPersonalizadoFornecedor>
            <URL>string</URL>
            <TITULO>string</TITULO>
            <TIPO>string</TIPO>
          </LinkPersonalizadoFornecedor>
          <LinkPersonalizadoFornecedor>
            <URL>string</URL>
            <TITULO>string</TITULO>
            <TIPO>string</TIPO>
          </LinkPersonalizadoFornecedor>
        </LinkPersonalizado>
        <BOrgLocalFaturamento>
          <BOrgLocalFaturamento>
            <CodigoBOrg>string</CodigoBOrg>
            <CampoVEnt>string</CampoVEnt>
            <FornecedorCliente>string</FornecedorCliente>
            <LocalFaturamentoCliente>string</LocalFaturamentoCliente>
            <Exclusao>string</Exclusao>
          </BOrgLocalFaturamento>
          <BOrgLocalFaturamento>
            <CodigoBOrg>string</CodigoBOrg>
            <CampoVEnt>string</CampoVEnt>
            <FornecedorCliente>string</FornecedorCliente>
            <LocalFaturamentoCliente>string</LocalFaturamentoCliente>
            <Exclusao>string</Exclusao>
          </BOrgLocalFaturamento>
        </BOrgLocalFaturamento>
      </msgFornecedor>
    </processarMensagemFornecedor>
  </soap12:Body>
```
> **Integração 4**    : Envio de Produto

```diff
+ **URL API ME POST** : https://api.me.com.br/MEBrokerWebService/MEBrokerWebService.asmx?op=processarMensagemProduto
```

```sh
<soap12:Body>
    <processarMensagemProduto xmlns="http://www.me.com.br/WebServices">
      <msgProduto>
        <IDINTEGRACAO>int</IDINTEGRACAO>
        <PRODUTO>int</PRODUTO>
        <DESCRICAO>string</DESCRICAO>
        <DESCRICAOCURTA>string</DESCRICAOCURTA>
        <COMPLEMENTO>string</COMPLEMENTO>
        <UNIDADE>string</UNIDADE>
        <MOEDA>string</MOEDA>
        <FABRICANTES>string</FABRICANTES>
        <FABRICANTES_COD>string</FABRICANTES_COD>
        <PRECOESTIMADO>double</PRECOESTIMADO>
        <PRAZOESTIMADO>int</PRAZOESTIMADO>
        <GRUPO_PRODUTO>string</GRUPO_PRODUTO>
        <CODIGO_GRUPO>string</CODIGO_GRUPO>
        <DESCRICAO_GRUPO>string</DESCRICAO_GRUPO>
        <CODIGO_FAMILIA>string</CODIGO_FAMILIA>
        <DESCRICAO_FAMILIA>string</DESCRICAO_FAMILIA>
        <GENERICO>string</GENERICO>
        <MARGEMTOLERANCIA>double</MARGEMTOLERANCIA>
        <CODPRODUTO>string</CODPRODUTO>
        <CODIGO>string</CODIGO>
        <FLOW>int</FLOW>
        <ITEMMRP>string</ITEMMRP>
        <NBM>string</NBM>
        <CONTARAZAO>string</CONTARAZAO>
        <ORIGEMMATERIAL>string</ORIGEMMATERIAL>
        <STATUS>string</STATUS>
        <CODCOMPRFUP>string</CODCOMPRFUP>
        <IMOBILIZADO>string</IMOBILIZADO>
        <FORADELINHA>string</FORADELINHA>
        <GERAPENDENCIA>string</GERAPENDENCIA>
        <ALTERACONTRATO>string</ALTERACONTRATO>
        <HOMOLOGACAO>string</HOMOLOGACAO>
        <GRUPODECOMPRAS>string</GRUPODECOMPRAS>
        <APLICACAO>string</APLICACAO>
        <CATEGORIAMATERIAL>string</CATEGORIAMATERIAL>
        <TIPOALTERACAO>string</TIPOALTERACAO>
        <REFERENCIAFABRICANTE>string</REFERENCIAFABRICANTE>
        <DESCRICAO_CURTA_40_PORTUGUES>string</DESCRICAO_CURTA_40_PORTUGUES>
        <DESCRICAO_LONGA_PT>string</DESCRICAO_LONGA_PT>
        <DESCRICAO_LONGA_EN>string</DESCRICAO_LONGA_EN>
        <UTILIZACODIGOLOF>string</UTILIZACODIGOLOF>
        <PDM>
          <CODIGOPDM>string</CODIGOPDM>
          <DESCRICAO_PT>string</DESCRICAO_PT>
          <DESCRICAO_EN>string</DESCRICAO_EN>
          <STATUSSOLICITACAO>string</STATUSSOLICITACAO>
          <Caracteristicas>
            <ProdutoPDMCaracteristica xsi:nil="true" />
            <ProdutoPDMCaracteristica xsi:nil="true" />
          </Caracteristicas>
        </PDM>
        <Caracteristicas>
          <ProdutoCaracteristica>
            <NUMORDEM>string</NUMORDEM>
            <DESCRICAO_PT>string</DESCRICAO_PT>
            <DESCRICAO_EN>string</DESCRICAO_EN>
            <VALOR_PT>string</VALOR_PT>
            <VALOR_EN>string</VALOR_EN>
          </ProdutoCaracteristica>
          <ProdutoCaracteristica>
            <NUMORDEM>string</NUMORDEM>
            <DESCRICAO_PT>string</DESCRICAO_PT>
            <DESCRICAO_EN>string</DESCRICAO_EN>
            <VALOR_PT>string</VALOR_PT>
            <VALOR_EN>string</VALOR_EN>
          </ProdutoCaracteristica>
        </Caracteristicas>
        <AplicacaoBOrg>
          <ProdutoAplicacaoBOrg>
            <BORG_FIELDNAME>string</BORG_FIELDNAME>
            <BORG_CODIGO>string</BORG_CODIGO>
            <APLICACAO>string</APLICACAO>
            <IVA>string</IVA>
            <CONTARAZAO>string</CONTARAZAO>
            <OI>string</OI>
            <PREEDITADO>string</PREEDITADO>
          </ProdutoAplicacaoBOrg>
          <ProdutoAplicacaoBOrg>
            <BORG_FIELDNAME>string</BORG_FIELDNAME>
            <BORG_CODIGO>string</BORG_CODIGO>
            <APLICACAO>string</APLICACAO>
            <IVA>string</IVA>
            <CONTARAZAO>string</CONTARAZAO>
            <OI>string</OI>
            <PREEDITADO>string</PREEDITADO>
          </ProdutoAplicacaoBOrg>
        </AplicacaoBOrg>
        <ProdutosBorgs>
          <ProdutoBOrg>
            <BORG_FIELDNAME>string</BORG_FIELDNAME>
            <BORG>string</BORG>
            <CODIGO>string</CODIGO>
            <PRAZOENTREGA>string</PRAZOENTREGA>
            <CONDICAOPAGAMENTO>string</CONDICAOPAGAMENTO>
            <TAXAIPI>double</TAXAIPI>
            <CUSTO>double</CUSTO>
            <FORNECEDORCLIENTE>string</FORNECEDORCLIENTE>
            <EXCLUIR>string</EXCLUIR>
          </ProdutoBOrg>
          <ProdutoBOrg>
            <BORG_FIELDNAME>string</BORG_FIELDNAME>
            <BORG>string</BORG>
            <CODIGO>string</CODIGO>
            <PRAZOENTREGA>string</PRAZOENTREGA>
            <CONDICAOPAGAMENTO>string</CONDICAOPAGAMENTO>
            <TAXAIPI>double</TAXAIPI>
            <CUSTO>double</CUSTO>
            <FORNECEDORCLIENTE>string</FORNECEDORCLIENTE>
            <EXCLUIR>string</EXCLUIR>
          </ProdutoBOrg>
        </ProdutosBorgs>
        <ProdutosAtributoWF>
          <ProdutoAtributoWF>
            <NOME>string</NOME>
            <TIPO>int</TIPO>
            <TAMANHO>int</TAMANHO>
            <OBRIGATORIO>string</OBRIGATORIO>
            <DESCRICAO>string</DESCRICAO>
            <AJUDA>string</AJUDA>
            <VALORES>string</VALORES>
            <VISIVELFORNECEDOR>string</VISIVELFORNECEDOR>
            <VALORDEFAULT>string</VALORDEFAULT>
          </ProdutoAtributoWF>
          <ProdutoAtributoWF>
            <NOME>string</NOME>
            <TIPO>int</TIPO>
            <TAMANHO>int</TAMANHO>
            <OBRIGATORIO>string</OBRIGATORIO>
            <DESCRICAO>string</DESCRICAO>
            <AJUDA>string</AJUDA>
            <VALORES>string</VALORES>
            <VISIVELFORNECEDOR>string</VISIVELFORNECEDOR>
            <VALORDEFAULT>string</VALORDEFAULT>
          </ProdutoAtributoWF>
        </ProdutosAtributoWF>
        <ContasRazao>
          <ProdutoContaRazao>
            <CONTA>string</CONTA>
            <EXCLUIR>string</EXCLUIR>
          </ProdutoContaRazao>
          <ProdutoContaRazao>
            <CONTA>string</CONTA>
            <EXCLUIR>string</EXCLUIR>
          </ProdutoContaRazao>
        </ContasRazao>
        <Grupos>
          <ProdutoGrupo>
            <InternalGrpID>int</InternalGrpID>
            <GRUPO_PRODUTO>string</GRUPO_PRODUTO>
            <CODIGO_GRUPO>string</CODIGO_GRUPO>
            <GRUPO_PRODUTO_PAI>string</GRUPO_PRODUTO_PAI>
            <CODIGO_GRUPO_PAI>string</CODIGO_GRUPO_PAI>
            <PERMITERELFORN>string</PERMITERELFORN>
            <CONTARAZAO>string</CONTARAZAO>
            <Atributos xsi:nil="true" />
          </ProdutoGrupo>
          <ProdutoGrupo>
            <InternalGrpID>int</InternalGrpID>
            <GRUPO_PRODUTO>string</GRUPO_PRODUTO>
            <CODIGO_GRUPO>string</CODIGO_GRUPO>
            <GRUPO_PRODUTO_PAI>string</GRUPO_PRODUTO_PAI>
            <CODIGO_GRUPO_PAI>string</CODIGO_GRUPO_PAI>
            <PERMITERELFORN>string</PERMITERELFORN>
            <CONTARAZAO>string</CONTARAZAO>
            <Atributos xsi:nil="true" />
          </ProdutoGrupo>
        </Grupos>
        <Ordens>
          <ProdutoOrdem>
            <ORDEM>string</ORDEM>
            <CATEGORIAORDEM>string</CATEGORIAORDEM>
          </ProdutoOrdem>
          <ProdutoOrdem>
            <ORDEM>string</ORDEM>
            <CATEGORIAORDEM>string</CATEGORIAORDEM>
          </ProdutoOrdem>
        </Ordens>
        <ContasContabil>
          <ProdutoContaContabil>
            <CONTACONTABIL>string</CONTACONTABIL>
          </ProdutoContaContabil>
          <ProdutoContaContabil>
            <CONTACONTABIL>string</CONTACONTABIL>
          </ProdutoContaContabil>
        </ContasContabil>
        <FabricantesCarga>
          <ProdutoFabricante>
            <CODIGOFABRICANTE>string</CODIGOFABRICANTE>
            <FABRICANTE>string</FABRICANTE>
          </ProdutoFabricante>
          <ProdutoFabricante>
            <CODIGOFABRICANTE>string</CODIGOFABRICANTE>
            <FABRICANTE>string</FABRICANTE>
          </ProdutoFabricante>
        </FabricantesCarga>
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
        <FornecedorFabricanteProduto>
          <FornecedorFabricanteProduto>
            <FORNECEDOR>string</FORNECEDOR>
            <FABRICANTE>string</FABRICANTE>
            <PERCENTUALPRODUTIVIDADE>double</PERCENTUALPRODUTIVIDADE>
          </FornecedorFabricanteProduto>
          <FornecedorFabricanteProduto>
            <FORNECEDOR>string</FORNECEDOR>
            <FABRICANTE>string</FABRICANTE>
            <PERCENTUALPRODUTIVIDADE>double</PERCENTUALPRODUTIVIDADE>
          </FornecedorFabricanteProduto>
        </FornecedorFabricanteProduto>
        <TIPOMATERIAL>string</TIPOMATERIAL>
        <SERVICO>string</SERVICO>
        <PERMITESUBITEM>string</PERMITESUBITEM>
        <IMPOSTOIVA>double</IMPOSTOIVA>
        <PrecoOrcadoBOrg>
          <ProdutoPrecoOrcadoBOrg>
            <BORG>int</BORG>
            <PRECOORCADO>double</PRECOORCADO>
          </ProdutoPrecoOrcadoBOrg>
          <ProdutoPrecoOrcadoBOrg>
            <BORG>int</BORG>
            <PRECOORCADO>double</PRECOORCADO>
          </ProdutoPrecoOrcadoBOrg>
        </PrecoOrcadoBOrg>
        <TipoDocumentoBOrg>
          <ProdutoTipoDocumentoBOrg>
            <CAMPOVENT>string</CAMPOVENT>
            <CODIGOBORG>string</CODIGOBORG>
            <TIPODOC>string</TIPODOC>
          </ProdutoTipoDocumentoBOrg>
          <ProdutoTipoDocumentoBOrg>
            <CAMPOVENT>string</CAMPOVENT>
            <CODIGOBORG>string</CODIGOBORG>
            <TIPODOC>string</TIPODOC>
          </ProdutoTipoDocumentoBOrg>
        </TipoDocumentoBOrg>
        <CATALOGOTRADUCAO>
          <ProdutoCatalogoTraducao>
            <IDIOMA>string</IDIOMA>
            <DESCRICAO>string</DESCRICAO>
            <COMPLEMENTO>string</COMPLEMENTO>
          </ProdutoCatalogoTraducao>
          <ProdutoCatalogoTraducao>
            <IDIOMA>string</IDIOMA>
            <DESCRICAO>string</DESCRICAO>
            <COMPLEMENTO>string</COMPLEMENTO>
          </ProdutoCatalogoTraducao>
        </CATALOGOTRADUCAO>
        <ConversaoUnidade>
          <ConversaoUnidade>
            <CODIGO_PRODUTO>string</CODIGO_PRODUTO>
            <UNIDADE_DE>string</UNIDADE_DE>
            <UNIDADE_PARA>string</UNIDADE_PARA>
            <QUANTIDADE_DE>double</QUANTIDADE_DE>
            <QUANTIDADE_PARA>double</QUANTIDADE_PARA>
            <CENTRO>string</CENTRO>
            <UNIDADEORIG>string</UNIDADEORIG>
            <UNIDADEDEST>string</UNIDADEDEST>
            <QUANTORIG>double</QUANTORIG>
            <QUANTDEST>double</QUANTDEST>
            <BORG_CODIGO>string</BORG_CODIGO>
            <TIPOALTERACAO>string</TIPOALTERACAO>
            <EXCLUIR>string</EXCLUIR>
          </ConversaoUnidade>
          <ConversaoUnidade>
            <CODIGO_PRODUTO>string</CODIGO_PRODUTO>
            <UNIDADE_DE>string</UNIDADE_DE>
            <UNIDADE_PARA>string</UNIDADE_PARA>
            <QUANTIDADE_DE>double</QUANTIDADE_DE>
            <QUANTIDADE_PARA>double</QUANTIDADE_PARA>
            <CENTRO>string</CENTRO>
            <UNIDADEORIG>string</UNIDADEORIG>
            <UNIDADEDEST>string</UNIDADEDEST>
            <QUANTORIG>double</QUANTORIG>
            <QUANTDEST>double</QUANTDEST>
            <BORG_CODIGO>string</BORG_CODIGO>
            <TIPOALTERACAO>string</TIPOALTERACAO>
            <EXCLUIR>string</EXCLUIR>
          </ConversaoUnidade>
        </ConversaoUnidade>
        <ProdutoConversaoUnidade>
          <ProdutoConversaoUnidade>
            <CODPRODUTO>string</CODPRODUTO>
            <CODIGO>string</CODIGO>
            <UNIDADEORIG>string</UNIDADEORIG>
            <UNIDADEDEST>string</UNIDADEDEST>
            <BORG_CODIGO>string</BORG_CODIGO>
            <QUANTORIG>double</QUANTORIG>
            <QUANTDEST>double</QUANTDEST>
            <TIPOALTERACAO>string</TIPOALTERACAO>
            <EXCLUIR>string</EXCLUIR>
          </ProdutoConversaoUnidade>
          <ProdutoConversaoUnidade>
            <CODPRODUTO>string</CODPRODUTO>
            <CODIGO>string</CODIGO>
            <UNIDADEORIG>string</UNIDADEORIG>
            <UNIDADEDEST>string</UNIDADEDEST>
            <BORG_CODIGO>string</BORG_CODIGO>
            <QUANTORIG>double</QUANTORIG>
            <QUANTDEST>double</QUANTDEST>
            <TIPOALTERACAO>string</TIPOALTERACAO>
            <EXCLUIR>string</EXCLUIR>
          </ProdutoConversaoUnidade>
        </ProdutoConversaoUnidade>
        <FornecedorProduto>
          <FornecedorProduto>
            <FORNECEDORCLIENTE>string</FORNECEDORCLIENTE>
            <CODIGO>string</CODIGO>
          </FornecedorProduto>
          <FornecedorProduto>
            <FORNECEDORCLIENTE>string</FORNECEDORCLIENTE>
            <CODIGO>string</CODIGO>
          </FornecedorProduto>
        </FornecedorProduto>
        <PRECOBASELINE>double</PRECOBASELINE>
        <NUMEROUNIDADESNAEMBALAGEM>double</NUMEROUNIDADESNAEMBALAGEM>
        <UrlImageFirst>string</UrlImageFirst>
      </msgProduto>
    </processarMensagemProduto>
  </soap12:Body>
```  
> **Integração 5**       : Pequisa de Fornecedor
  
```diff  
+ **URL API SIENGE GET** : https://api.sienge.com.br/produtoeinovacao/public/api/v1/creditors/{creditorId}
```
```sh
{
    "id": 1,
    "name": "Domiceq",
    "tradeName": "Domiceq",
    "cpf": null,
    "cnpj": "96.604.963/0001-73",
    "supplier": "S",
    "broker": "N",
    "employee": "N",
    "links": [
        {
            "rel": "bank-informations",
            "href": "/sienge/api/v1/creditors/1/bank-informations"
        }
    ]
}
```

> **Integração 6**    : Pesquisa de Produto

```diff
- **URL API SIENGE GET** : https://api.sienge.com.br/produtoeinovacao/public/api/v1/?????

- Não encontamos no cardeno de APIs SIENGE (https://api.sienge.com.br/docs)
```

## Contrato de Request - PRESTES - Criação de Cotação

>Este Contrato de Request, baseado na disponibilidade de atributos apresentado na API **processarMensagemRequisicao**, define quais são os atributos que serão enviados, os tipo de valores, e os domínios caso exista, os campos requeridos pelo ME para atender a está requisição também devem ser definodos neste contrato:

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

## Contrato de Response - PRESTES - Pré Pedido de Cotação

>Este Contrato de Response, baseado na disponibilidade de atributos apresentado na API **getMessagePrePedidoResponse**,  define quais são os atributos que serão enviados, os tipo de valores, e o domínio caso exista, os campos requeridos pelo SIENGE para atender a está requisição também devem ser definodos neste contrato:

```sh
  <soap12:Body>
    <getMessagePrePedidoResponse xmlns="http://www.me.com.br/WebServices">
      <getMessagePrePedidoResult>
        <Token>string</Token>
        <Message>
	  ...
	  <Atributos>
	  ...
	  <BOrgs>
	  ...
	  <Itens>
	  ...
	  <RequisicoesPrePedido>
	  ...
	  <CotacoesPrePedido>
	  ...
	  <MsgFornecedor>
	  ...
	  <FormasPagamento>
	  ...
	  <AprovadoresPrePedido>
	  ...
          <LocaisEntregaPrePedido>
	  ...
          <LocaisCobrancaPrePedido>
	  ...
	  <Propriedades>
	  ...
	  <Objetos>
	  ...
	  <Textos>
	  ...
	  <RelatorioNegociacao>
	  ...
          <CustoAdicional>
	  ...
	  <RequisicaoID>int</RequisicaoID>
	  ...
	  <ColetaPreco>
	  ...
	</Message>
      </getMessagePrePedidoResult>
    </getMessagePrePedidoResponse>
  </soap12:Body>
```         
## Contrato de Request - PRESTES - Fornecedor

>Este Contrato de Response, baseado na disponibilidade de atributos apresentado na API **processarMensagemFornecedor**,  define quais são os atributos que serão enviados, os tipo de valores, e o domínio caso exista, os campos requeridos pelo SIENGE para atender a está requisição também devem ser definodos neste contrato:

```sh
<soap12:Body>
    <processarMensagemFornecedor xmlns="http://www.me.com.br/WebServices">
      <msgFornecedor>
        ...
        <ContatosBorg>
          <ContatosBorg>
            ...
          </ContatosBorg>
          <ContatosBorg>
            ...
          </ContatosBorg>
        </ContatosBorg>
      ...
          <FornecedorBOrg>
            <CodigoBOrg>string</CodigoBOrg>
            <CampoVEnt>string</CampoVEnt>
           ....
          </FornecedorBOrg>
          <FornecedorBOrg>
            <CodigoBOrg>string</CodigoBOrg>
            <CampoVEnt>string</CampoVEnt>
            ...
          </FornecedorBOrg>
        </BOrgItens>
        <ContasCorrente>
          <FornecedorContaCorrente>
            <CodigoConta>string</CodigoConta>
            <Principal>string</Principal>
          </FornecedorContaCorrente>
          <FornecedorContaCorrente>
            <CodigoConta>string</CodigoConta>
            <Principal>string</Principal>
          </FornecedorContaCorrente>
        </ContasCorrente>
        <GruposProduto>
          <FornecedorGrupoProduto>
            <CodigoGrupo>string</CodigoGrupo>
            <DescricaoGrupo>string</DescricaoGrupo>
          </FornecedorGrupoProduto>
          <FornecedorGrupoProduto>
            <CodigoGrupo>string</CodigoGrupo>
            <DescricaoGrupo>string</DescricaoGrupo>
          </FornecedorGrupoProduto>
        </GruposProduto>
        <FornecedorEstrategico>string</FornecedorEstrategico>
        <FornecedorContas>
          <FornecedorContas>
            <Id>int</Id>
            <Fornecedor>int</Fornecedor>
            <Banco>string</Banco>
            <Agencia>string</Agencia>
            <Conta>string</Conta>
            <DigitoAgencia>string</DigitoAgencia>
            <DigitoConta>string</DigitoConta>
            <NomeCorrentista>string</NomeCorrentista>
            <Ativo>string</Ativo>
          </FornecedorContas>
          <FornecedorContas>
            <Id>int</Id>
            <Fornecedor>int</Fornecedor>
            <Banco>string</Banco>
            <Agencia>string</Agencia>
            <Conta>string</Conta>
            <DigitoAgencia>string</DigitoAgencia>
            <DigitoConta>string</DigitoConta>
            <NomeCorrentista>string</NomeCorrentista>
            <Ativo>string</Ativo>
          </FornecedorContas>
        </FornecedorContas>
        <IDF>double</IDF>
        <Atributos>
          <RespostaAtributoMeusFornecedores>
            <ID>int</ID>
            <Fornecedor>int</Fornecedor>
            <Nome>string</Nome>
            <Valor>string</Valor>
            <Descricao>string</Descricao>
          </RespostaAtributoMeusFornecedores>
          <RespostaAtributoMeusFornecedores>
            <ID>int</ID>
            <Fornecedor>int</Fornecedor>
            <Nome>string</Nome>
            <Valor>string</Valor>
            <Descricao>string</Descricao>
          </RespostaAtributoMeusFornecedores>
        </Atributos>
        ...
        <EmailsPorProcesso>
          <EmailProcesso>
            <Processo>string</Processo>
            <EMail>string</EMail>
          </EmailProcesso>
          <EmailProcesso>
            <Processo>string</Processo>
            <EMail>string</EMail>
          </EmailProcesso>
        </EmailsPorProcesso>
       ...
        <BOrgPgtoItens>
          <BOrgPgtoItens>
            <CodigoBOrg>string</CodigoBOrg>
            <CampoVEnt>string</CampoVEnt>
            ...
          </BOrgPgtoItens>
          <BOrgPgtoItens>
            <CodigoBOrg>string</CodigoBOrg>
            <CampoVEnt>string</CampoVEnt>
            ...
          </BOrgPgtoItens>
        </BOrgPgtoItens>
        <LinkPersonalizado>
          <LinkPersonalizadoFornecedor>
            ...
          </LinkPersonalizadoFornecedor>
          <LinkPersonalizadoFornecedor>
            ...
          </LinkPersonalizadoFornecedor>
        </LinkPersonalizado>
        <BOrgLocalFaturamento>
          <BOrgLocalFaturamento>
            <CodigoBOrg>string</CodigoBOrg>
            <CampoVEnt>string</CampoVEnt>
            <FornecedorCliente>string</FornecedorCliente>
            <LocalFaturamentoCliente>string</LocalFaturamentoCliente>
            <Exclusao>string</Exclusao>
          </BOrgLocalFaturamento>
          <BOrgLocalFaturamento>
            <CodigoBOrg>string</CodigoBOrg>
            <CampoVEnt>string</CampoVEnt>
            <FornecedorCliente>string</FornecedorCliente>
            <LocalFaturamentoCliente>string</LocalFaturamentoCliente>
            <Exclusao>string</Exclusao>
          </BOrgLocalFaturamento>
        </BOrgLocalFaturamento>
      </msgFornecedor>
    </processarMensagemFornecedor>
  </soap12:Body>
```
## Contrato de Request - PRESTES - Produto

>Este Contrato de Response, baseado na disponibilidade de atributos apresentado na API **processarMensagemProduto**,  define quais são os atributos que serão enviados, os tipo de valores, e o domínio caso exista, os campos requeridos pelo SIENGE para atender a está requisição também devem ser definodos neste contrato:

```sh
<soap12:Body>
    <processarMensagemProduto xmlns="http://www.me.com.br/WebServices">
      <msgProduto>
        ...
          <Caracteristicas>
            <ProdutoPDMCaracteristica xsi:nil="true" />
            <ProdutoPDMCaracteristica xsi:nil="true" />
          </Caracteristicas>
        </PDM>
        <Caracteristicas>
          <ProdutoCaracteristica>
            ...
          </ProdutoCaracteristica>
          <ProdutoCaracteristica>
           ...
          </ProdutoCaracteristica>
        </Caracteristicas>
        <AplicacaoBOrg>
          <ProdutoAplicacaoBOrg>
            ...
          </ProdutoAplicacaoBOrg>
          <ProdutoAplicacaoBOrg>
            ...
          </ProdutoAplicacaoBOrg>
        </AplicacaoBOrg>
        <ProdutosBorgs>
          <ProdutoBOrg>
            ...
          </ProdutoBOrg>
          <ProdutoBOrg>
            ...
          </ProdutoBOrg>
        </ProdutosBorgs>
        <ProdutosAtributoWF>
          <ProdutoAtributoWF>
            ...
          </ProdutoAtributoWF>
          <ProdutoAtributoWF>
            ...
          </ProdutoAtributoWF>
        </ProdutosAtributoWF>
        <ContasRazao>
          <ProdutoContaRazao>
            ..
          </ProdutoContaRazao>
          <ProdutoContaRazao>
            ...
          </ProdutoContaRazao>
        </ContasRazao>
        <Grupos>
          <ProdutoGrupo>
            <InternalGrpID>int</InternalGrpID>
          ...
            <Atributos xsi:nil="true" />
          </ProdutoGrupo>
          <ProdutoGrupo>
            <InternalGrpID>int</InternalGrpID>
            ...
            <Atributos xsi:nil="true" />
          </ProdutoGrupo>
        </Grupos>
        <Ordens>
          <ProdutoOrdem>
            ...
          </ProdutoOrdem>
          <ProdutoOrdem>
            ...
          </ProdutoOrdem>
        </Ordens>
        <ContasContabil>
          <ProdutoContaContabil>
            ...
          </ProdutoContaContabil>
          <ProdutoContaContabil>
            ...
          </ProdutoContaContabil>
        </ContasContabil>
        <FabricantesCarga>
          <ProdutoFabricante>
            ...
          </ProdutoFabricante>
          <ProdutoFabricante>
            ...
          </ProdutoFabricante>
        </FabricantesCarga>
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
        <FornecedorFabricanteProduto>
          <FornecedorFabricanteProduto>
           ...
          </FornecedorFabricanteProduto>
          <FornecedorFabricanteProduto>
           ...
          </FornecedorFabricanteProduto>
        </FornecedorFabricanteProduto>
       ...
        <PrecoOrcadoBOrg>
          <ProdutoPrecoOrcadoBOrg>
           ...
          </ProdutoPrecoOrcadoBOrg>
          <ProdutoPrecoOrcadoBOrg>
            ...
          </ProdutoPrecoOrcadoBOrg>
        </PrecoOrcadoBOrg>
        <TipoDocumentoBOrg>
          <ProdutoTipoDocumentoBOrg>
            ...
          </ProdutoTipoDocumentoBOrg>
          <ProdutoTipoDocumentoBOrg>
            ...
          </ProdutoTipoDocumentoBOrg>
        </TipoDocumentoBOrg>
        ...
          <ProdutoCatalogoTraducao>
           ...
          </ProdutoCatalogoTraducao>
          <ProdutoCatalogoTraducao>
           ...
          </ProdutoCatalogoTraducao>
        ...
        <ConversaoUnidade>
          <ConversaoUnidade>
            ...
          </ConversaoUnidade>
          <ConversaoUnidade>
            ...
          </ConversaoUnidade>
        </ConversaoUnidade>
        <ProdutoConversaoUnidade>
          <ProdutoConversaoUnidade>
            ...
          </ProdutoConversaoUnidade>
          <ProdutoConversaoUnidade>
            ...
          </ProdutoConversaoUnidade>
        </ProdutoConversaoUnidade>
        <FornecedorProduto>
          <FornecedorProduto>
            ...
          </FornecedorProduto>
          <FornecedorProduto>
            ...
          </FornecedorProduto>
        </FornecedorProduto>
       ...
      </msgProduto>
    </processarMensagemProduto>
  </soap12:Body>
```  


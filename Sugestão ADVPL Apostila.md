# ![ADVPL Web Protheus](https://drive.google.com/uc?export=view&id=1j7DlkhrP2i3ocKsC5bQn_0ZAw6zrPIj6)

#### Exemplo de Código ADVPL com Botão de Copiar --- Opção 1: bloco de código nativo do markdown (Menos esforço aplicado)

```
#Include "TOTVS.CH"

// Função principal do programa
User Function Main()
    Local aMenu := {}
    
    // Construção do menu
    AAdd(aMenu, {"1. Cadastrar Cliente", {|| CadastroCliente()}})
    AAdd(aMenu, {"2. Consultar Cliente", {|| ConsultaCliente()}})
    AAdd(aMenu, {"3. Sair", {|| MsgInfo("Saindo do sistema...")}})
    
    // Mostra o menu
    While .T.
        Local cOpcao := MenuTitle("Menu Principal", aMenu, .T.)
        Eval(aMenu[Val(cOpcao)][2])
        If Val(cOpcao) == 3
            Exit
        EndIf
    EndWhile
    
    Return
End Function

// Função para cadastrar cliente
Static Function CadastroCliente()
    Local cCodigo := Space(10)
    Local cNome := Space(50)
    Local cTelefone := Space(15)
    Local aCliente := {}
    
    @ 01, 02 SAY "Cadastro de Cliente" COLOR "W+/B"
    @ 03, 02 SAY "Código:" GET cCodigo PICTURE "@!"
    @ 04, 02 SAY "Nome:" GET cNome PICTURE "@!"
    @ 05, 02 SAY "Telefone:" GET cTelefone PICTURE "@!"
    READ
    
    If Empty(cCodigo) .OR. Empty(cNome)
        MsgStop("Código e Nome são obrigatórios!")
    Else
        aCliente := {cCodigo, cNome, cTelefone}
        DbUseArea(.T., "DBFNTX", "Clientes", .T., .T.)
        DbAppend()
        FIELD->CODIGO := aCliente[1]
        FIELD->NOME := aCliente[2]
        FIELD->TELEFONE := aCliente[3]
        DbCloseArea()
        MsgInfo("Cliente cadastrado com sucesso!")
    EndIf
    
    Return
End Function

// Função para consultar clientes
Static Function ConsultaCliente()
    Local aDados := {}
    Local nLinha := 3
    
    DbUseArea(.T., "DBFNTX", "Clientes", .T., .F.)
    
    If !DbGoTop()
        MsgStop("Não há clientes cadastrados!")
        Return
    EndIf
    
    @ 01, 02 CLEAR
    @ 01, 02 SAY "Consulta de Clientes" COLOR "W+/B"
    @ 02, 02 SAY "Código     Nome                     Telefone" COLOR "W+/B"
    
    While !Eof()
        aDados := {FIELD->CODIGO, FIELD->NOME, FIELD->TELEFONE}
        @ nLinha, 02 SAY PadR(aDados[1], 10) + " " + PadR(aDados[2], 25) + " " + PadR(aDados[3], 15)
        nLinha++
        DbSkip()
    EndDo
    
    DbCloseArea()
    
    Return
End Function
```

### Exemplo de Código ADVPL com Botão de Copiar --- Opção 2: Criando uma página HTML e publicando-a em hospedagem gratuita, por exemplo, o GitHub Pages (Mais esforço aplicado)

<a href="https://matheusmoraes10.github.io/SugestaoUniversidadeTOTVS/">https://matheusmoraes10.github.io/SugestaoUniversidadeTOTVS/</a>

### Opção 3 --- Baixe o arquivo e um leitor de Markdown, como o Typedown, por exemplo. E Utilize como se fosse um PDF.

<a href="https://apps.microsoft.com/detail/9p8tcw4h2hb4?hl=en-US&gl=BR">https://apps.microsoft.com/detail/9p8tcw4h2hb4?hl=en-US&gl=BR</a>



<h2>Exemplo de conteudo escrito</h2>
<p>
Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores est sint obcaecati beatae possimus blanditiis laudantium distinctio? Alias similique odit impedit quaerat ducimus molestiae reiciendis ipsa, harum laboriosam quos eius, quas pariatur, sunt provident ut numquam corrupti? Voluptatum soluta facere error reprehenderit officiis dolor voluptatem laudantium sapiente consequuntur libero accusamus aliquid, est molestiae, saepe quasi assumenda beatae quae ab architecto? Quasi numquam labore ratione quod commodi, sunt perferendis cumque dolore aut magnam ut, autem aperiam aliquam. Sapiente nesciunt odit vitae dicta modi praesentium accusantium! Obcaecati velit impedit voluptates deleniti veniam quas, dolorem earum rerum maxime, animi consequatur odio, assumenda illo!
</p>

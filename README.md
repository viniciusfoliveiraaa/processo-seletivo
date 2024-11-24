
 **Cenários em BDD**
 
 **Feature: Login

 > * Scenario: Login com credenciais válidas
    Given que o usuário está na página de login
    When o usuário insere "standard_user" no campo de usuário
    And insere "secret_sauce" no campo de senha
    And clica no botão "Login"
    Then o usuário é redirecionado para a página de produtos.*

  > * Scenario: Login com credenciais inválidas
    Given que o usuário está na página de login
    When o usuário insere "usuario_invalido" no campo de usuário
    And insere "senha_errada" no campo de senha
    And clica no botão "Login"
    Then uma mensagem de erro "Username and password do not match" é exibida .*

  Scenario: Login com campos vazios
    Given que o usuário está na página de login
    When o usuário clica no botão "Login" sem preencher os campos
    Then uma mensagem de erro "Username is required" é exibida*

> *Feature: Produtos *

  Scenario: Listar todos os produtos
    Given que o usuário está na página de produtos
    When a página é carregada
    Then todos os produtos disponíveis são exibidos com nome, preço e imagem

  Scenario: Adicionar um produto ao carrinho
    Given que o usuário está na página de produtos
    When o usuário clica no botão "Add to cart" do produto "Sauce Labs Backpack"
    Then o contador do carrinho exibe "1"

  Scenario: Ordenar produtos por preço (do menor para o maior)
    Given que o usuário está na página de produtos
    When o usuário seleciona "Price (low to high)" na opção de ordenação
    Then os produtos são exibidos em ordem crescente de preço

>* Feature: Carrinho de compras*

  Scenario: Verificar itens no carrinho após logout e login
    Given que o usuário adicionou itens ao carrinho
    And o usuário faz logout
    When o usuário faz login novamente
    Then os itens no carrinho devem ser mantidos

  Scenario: Realizar checkout com sucesso
    Given que o usuário adicionou itens ao carrinho
    And o usuário acessa a página do carrinho
    When o usuário clica em "Checkout"
    And preenche os campos obrigatórios "First Name", "Last Name", e "Postal Code"
    And clica em "Continue" e depois "Finish"
    Then uma mensagem "Thank you for your order!" é exibida

  Scenario: Finalizar compra com campos obrigatórios ausentes
    Given que o usuário adicionou itens ao carrinho
    And o usuário acessa a página do carrinho
    When o usuário clica em "Checkout"
    And deixa os campos obrigatórios vazios
    Then uma mensagem de erro "Error: First Name is required" é exibida*


> *Feature: Performance do site*

  Scenario: Tempo de carregamento da página inicial
    Given que o usuário acessa o site
    When a página inicial é carregada
    Then o tempo de carregamento deve ser inferior a 3 segundos

  Scenario: Redimensionamento em dispositivos móveis
    Given que o usuário acessa o site em diferentes dispositivos
    When o tamanho da tela é alterado
    Then o layout deve se ajustar corretamente ao dispositivo


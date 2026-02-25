

import java.util.Scanner;

public class Sisteminha {

    static Scanner scanner = new Scanner(System.in);

    static String[] clientes = new String[10];
    static int totalClientes = 0;

    static double caixa = 0.00;

    static String[] produtos = {
            "Shampoo",
            "Condicionador",
            "Máscara",
            "Creme para Pentear",
            "Gelatina Capilar"
    };

    static double[] precos = {30.00, 35.00, 60.00, 45.00, 25.00};
    static int[] estoque = {50, 50, 30, 60, 15};

    public static void main(String[] args) {

        if (!login()) {
            return;
        }

        int opcao;

        do {
            menu();
            opcao = scanner.nextInt();

            switch (opcao) {
                case 1:
                    mostrarProdutos();
                    break;
                case 2:
                    mostrarClientes();
                    break;
                case 3:
                    cadastrarCliente();
                    break;
                case 4:
                    mostrarCaixa();
                    break;
                case 5:
                    venderProduto();
                    break;
                case 6:
                    limparTela();
                    break;
                case 7:
                    System.out.println("Saindo da loja...");
                    break;
                default:
                    System.out.println("Opção inválida!");
            }

        } while (opcao != 7);
    }

    public static boolean login() {
        System.out.println("=== LOGIN DO SISTEMA ===");
        System.out.print("Informe seu usuário: ");
        String login = scanner.nextLine();

        System.out.print("Senha: ");
        String senha = scanner.nextLine();

        if (login.equals("admin") && senha.equals("123")) {
            System.out.println("Login realizado");
            return true;
        } else {
            System.out.println("Usuário ou senha incorreto");
            return false;
        }
    }

    public static void menu() {
        System.out.println("\n=== MENU ===");
        System.out.println("1 - Mostrar produtos em estoque");
        System.out.println("2 - Mostrar clientes");
        System.out.println("3 - Cadastrar novo cliente");
        System.out.println("4 - Mostrar dinheiro no caixa");
        System.out.println("5 - Vender produto");
        System.out.println("6 - Limpar tela");
        System.out.println("7 - Sair");
        System.out.print("Escolha uma opção: ");
    }

    public static void mostrarProdutos() {
        System.out.println("\n=== PRODUTOS ===");

        for (int i = 0; i < produtos.length; i++) {
            System.out.println("ID: 0" + (i + 1) +
                    " | Produto: " + produtos[i] +
                    " | Preço: R$" + precos[i] +
                    " | Estoque: " + estoque[i]);
        }

        voltarOuSair();
    }

    public static void mostrarClientes() {
        System.out.println("\n=== CLIENTES ===");

        for (int i = 0; i < 10; i++) {
            System.out.println("ID: " + (i + 1) + " Cliente: " +
                    (clientes[i] == null ? "" : clientes[i]));
        }

        voltarOuSair();
    }

    public static void cadastrarCliente() {
        if (totalClientes < 10) {
            scanner.nextLine();
            System.out.print("Digite o nome do cliente: ");
            String nome = scanner.nextLine();

            clientes[totalClientes] = nome;
            totalClientes++;

            System.out.println("Cadastro realizado com sucesso!");
        } else {
            System.out.println("Limite de clientes atingido.");
        }

        voltarOuSair();
    }

    public static void mostrarCaixa() {
        System.out.println("Dinheiro no caixa: R$" + caixa);
        voltarOuSair();
    }

    public static void venderProduto() {

        System.out.println("\n=== TELA DE VENDA ===");

        // Mostrar produtos
        for (int i = 0; i < produtos.length; i++) {
            System.out.println("ID: " + (i + 1) +
                    " | Produto: " + produtos[i] +
                    " | Preço: R$" + precos[i] +
                    " | Estoque: " + estoque[i]);
        }

        int id;

        // Validar ID
        while (true) {
            System.out.print("\nQual produto deseja comprar? ");

            if (scanner.hasNextInt()) {
                id = scanner.nextInt();

                if (id >= 1 && id <= produtos.length) {
                    break;
                } else {
                    System.out.println("Opção inválida. Digite um ID válido.");
                }
            } else {
                System.out.println("Opção inválida. Digite um número.");
                scanner.next(); // limpa erro
            }
        }

        int quantidade;

        // Validar quantidade
        while (true) {
            System.out.print("Qual a quantidade  de produtos deseja comprar? ");

            if (scanner.hasNextInt()) {
                quantidade = scanner.nextInt();

                if (quantidade <= 0) {
                    System.out.println("Digite uma quantidade.");
                }
                else if (quantidade > estoque[id - 1]) {
                    System.out.println("Quantidade sem estoque.");
                }
                else {
                    break;
                }
            } else {
                System.out.println("Digite apenas números.");
                scanner.next();
            }
        }

        double total = precos[id - 1] * quantidade;

        System.out.println("\nProduto: " + produtos[id - 1]);
        System.out.println("Quantidade: " + quantidade);
        System.out.println("Total: R$" + total);

        System.out.print("Confirmar sua compra? (1 = Sim / 0 = Não): ");
        int confirmar = scanner.nextInt();

        if (confirmar == 1) {
            estoque[id - 1] -= quantidade;
            caixa += total;
            System.out.println("Compra realizada!");
        } else {
            System.out.println("Compra cancelada.");
        }

        voltarOuSair();
    }

    public static void limparTela() {
        for (int i = 0; i < 30; i++) {
            System.out.println();
        }
    }

    public static void voltarOuSair() {
        System.out.println("\n0 - Sair");
        System.out.println("1 - Voltar ao menu");

        int escolha = scanner.nextInt();

        if (escolha == 0) {
            System.out.println("Saindo...");
            System.exit(0);
        }
    }
}
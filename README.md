package org.example;

public class Main {
    public static void main(String[] args) {
        Camiseta simples = new CamisetaSimples("M", "Branca", 50.0);
        Camiseta estampada = new CamisetaEstampada("G", "Preta", 80.0, "Dragão");
        simples.exibirDetalhes();
        System.out.println("Preço com desconto: R$ " + simples.calcularDesconto());
        System.out.println("\n---\n");
        estampada.exibirDetalhes();
        System.out.println("Preço com desconto: R$ " + estampada.calcularDesconto());
    }
}

package org.example;

public abstract class Camiseta {
    private String tamanho;
    private String cor;
    private double preco;
    public Camiseta(String tamanho, String cor, double preco) {
        this.tamanho = tamanho;
        this.cor = cor;
        this.preco = preco;
    }
    public String getTamanho() {
        return tamanho;
    }
    public void setTamanho(String tamanho) {
        this.tamanho = tamanho;
    }
    public String getCor() {
        return cor;
    }
    public void setCor(String cor) {
        this.cor = cor;
    }
    public double getPreco() {
        return preco;
    }
    public void setPreco(double preco) {
        this.preco = preco;
    }
    public void exibirDetalhes() {
        System.out.println("Tamanho: " + tamanho);
        System.out.println("Cor: " + cor);
        System.out.println("Preço: R$ " + preco);
    }
    public abstract double calcularDesconto();
}

package org.example;

public class CamisetaSimples extends Camiseta {
    public CamisetaSimples(String tamanho, String cor, double preco) {
        super(tamanho, cor, preco);
    }
    @Override
    public double calcularDesconto() {
        return getPreco() * 0.90; // 10% de desconto
    }
}

package org.example;

public class CamisetaEstampada extends Camiseta {

    private String estampa;

    public CamisetaEstampada(String tamanho, String cor, double preco, String estampa) {
        super(tamanho, cor, preco);
        this.estampa = estampa;
    }
    public String getEstampa() {
        return estampa;
    }
    public void setEstampa(String estampa) {
        this.estampa = estampa;
    }
    @Override
    public void exibirDetalhes() {
        super.exibirDetalhes();
        System.out.println("Estampa: " + estampa);
    }
    @Override
    public double calcularDesconto() {
        return getPreco() * 0.95; // 5% de desconto
    }
}

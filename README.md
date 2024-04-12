# Construindo-um-Sistema-para-um-Estacionamento-com-C-
Instruções para construção de um sistema de estacionamento em C#. Aqui estão os passos que podemos seguir para criar esse projeto:

1. **Defina os requisitos**:
   Comece definindo os requisitos do sistema de estacionamento. Quais funcionalidades ele deve ter? Por exemplo, adicionar veículos, remover veículos, calcular o valor cobrado durante o período, listar veículos etc.

2. **Crie uma classe para representar os veículos**:
   Crie uma classe chamada `Veiculo` com propriedades como placa, modelo, cor e tipo (carro, moto, caminhão etc.). Essa classe será usada para criar objetos que representam os veículos estacionados.

3. **Implemente a lógica de adicionar veículos**:
   Crie um método para adicionar um veículo ao sistema. Você pode usar uma lista para armazenar os veículos estacionados.

4. **Implemente a lógica de remoção de veículos**:
   Crie um método para remover um veículo do sistema com base na placa ou em outra identificação única.

5. **Calcule o valor cobrado durante o período**:
   Se o seu estacionamento cobra por hora, implemente a lógica para calcular o valor com base no tempo que o veículo ficou estacionado.

6. **Liste os veículos estacionados**:
   Crie um método para listar todos os veículos estacionados no momento.

7. **Teste o seu sistema**:
   Crie um programa principal (método `Main`) para testar todas as funcionalidades do seu sistema. Adicione alguns veículos, remova outros e verifique se o cálculo do valor está correto.

8. **Utilize uma IDE**:
   Use uma ferramenta de desenvolvimento integrado (IDE) como o Visual Studio ou o Visual Studio Code para escrever e executar o seu código.

Lembre-se de seguir as boas práticas de programação, como dividir o código em classes, usar comentários para explicar a lógica e testar cada funcionalidade separadamente. 

Claro! Aqui está um exemplo básico de como você pode implementar o sistema de estacionamento em C#:

```csharp
using System;
using System.Collections.Generic;

namespace Estacionamento
{
    class Veiculo
    {
        public string Placa { get; set; }
        public string Modelo { get; set; }
        public string Cor { get; set; }
        public string Tipo { get; set; }
    }

    class Program
    {
        static List<Veiculo> veiculosEstacionados = new List<Veiculo>();

        static void Main(string[] args)
        {
            while (true)
            {
                Console.WriteLine("Escolha uma opção:");
                Console.WriteLine("1. Adicionar veículo");
                Console.WriteLine("2. Remover veículo");
                Console.WriteLine("3. Listar veículos");
                Console.WriteLine("4. Sair");

                int opcao = int.Parse(Console.ReadLine());

                switch (opcao)
                {
                    case 1:
                        AdicionarVeiculo();
                        break;
                    case 2:
                        RemoverVeiculo();
                        break;
                    case 3:
                        ListarVeiculos();
                        break;
                    case 4:
                        Environment.Exit(0);
                        break;
                    default:
                        Console.WriteLine("Opção inválida. Tente novamente.");
                        break;
                }
            }
        }

        static void AdicionarVeiculo()
        {
            Console.WriteLine("Digite a placa do veículo:");
            string placa = Console.ReadLine();

            Console.WriteLine("Digite o modelo do veículo:");
            string modelo = Console.ReadLine();

            Console.WriteLine("Digite a cor do veículo:");
            string cor = Console.ReadLine();

            Console.WriteLine("Digite o tipo do veículo (carro, moto, caminhão etc.):");
            string tipo = Console.ReadLine();

            Veiculo novoVeiculo = new Veiculo
            {
                Placa = placa,
                Modelo = modelo,
                Cor = cor,
                Tipo = tipo
            };

            veiculosEstacionados.Add(novoVeiculo);
            Console.WriteLine("Veículo adicionado com sucesso!");
        }

        static void RemoverVeiculo()
        {
            Console.WriteLine("Digite a placa do veículo a ser removido:");
            string placa = Console.ReadLine();

            Veiculo veiculoRemovido = veiculosEstacionados.Find(v => v.Placa == placa);

            if (veiculoRemovido != null)
            {
                veiculosEstacionados.Remove(veiculoRemovido);
                Console.WriteLine("Veículo removido com sucesso!");
            }
            else
            {
                Console.WriteLine("Veículo não encontrado.");
            }
        }

        static void ListarVeiculos()
        {
            Console.WriteLine("Veículos estacionados:");
            foreach (var veiculo in veiculosEstacionados)
            {
                Console.WriteLine($"Placa: {veiculo.Placa}, Modelo: {veiculo.Modelo}, Cor: {veiculo.Cor}, Tipo: {veiculo.Tipo}");
            }
        }
    }
}
```

Este é apenas um exemplo básico para que possamos começar. Podemos expandir e aprimorar o sistema conforme nossas necessidades. Lembre-se de adicionar tratamento de erros, persistência de dados (por exemplo, salvar os veículos em um arquivo ou banco de dados) e outras funcionalidades específicas desse projeto.

Para calcular o valor cobrado por hora no sistema de estacionamento, podemos seguir os seguintes passos:

1. **Defina a taxa por hora**:
   Primeiro, defina qual será a taxa cobrada por hora de estacionamento. Por exemplo, se você cobra R$ 5,00 por hora, esse será o valor base para o cálculo.

2. **Registre o horário de entrada do veículo**:
   Quando um veículo entrar no estacionamento, registre o horário exato em que ele entrou. Você pode usar a classe `DateTime` do C# para obter a data e a hora atual.

3. **Registre o horário de saída do veículo**:
   Quando o veículo sair, registre o horário de saída. Subtraia o horário de saída pelo horário de entrada para obter o tempo total que o veículo ficou estacionado.

4. **Calcule o valor com base no tempo**:
   Multiplique o tempo total (em horas) pelo valor da taxa por hora. Por exemplo:
   ```
   Tempo total = Horário de saída - Horário de entrada
   Valor cobrado = Tempo total * Taxa por hora
   ```

5. **Exiba o valor para o cliente**:
   Mostre o valor calculado ao cliente quando ele for retirar o veículo.

Considerando sempre o arredondamentos (por exemplo, arredondar para cima se o tempo for maior que 30 minutos) e de lidar com situações especiais, como veículos que ficam estacionados durante a noite. Você pode ajustar essas regras conforme necessário para o seu sistema específico.

https://github.com/digitalinnovationone/trilha-net-fundamentos-desafio

# Diagrama:
## Questão: Dado o contexto abaixo, defina as tabelas a serem criadas, indicando as chaves primárias, os tipos de dados a serem utilizados nos elementos de dados e os relacionamentos (chave estrangeira) entre as entidades (tabelas). O negócio principal da locadora de automóveis “Carro Bom” é a o aluguel de carros. A locadora possui várias filiais. Carros possuem modelos e possuem características que permitem classificá-los em grupos. Por exemplo, o grupo Econômico inclui os modelos Gol, Palio e Celta, motor 1.0, sem ar condicionado. Os valores das diárias são dados pelo grupo do carro alugado. De um dado modelo, a locadora pode possuir vários carros. Sobre um carro específico desejase saber várias informações, tais como: placa, nº do chassi, RENAVAM, ano de fabricação, potência do motor, cor, número de portas e equipamentos (p.ex., ar condicionado, direção hidráulica, freios ABS, Air bag, rádio). Além disso, deseja-se saber em que filial um carro específico está lotado no momento. Clientes podem efetuar reservas. Um cliente pode ser uma pessoa física ou uma pessoa jurídica. Na reserva deve-se registrar a filial de retirada e a filial de devolução do veículo, a data e a hora pretendida para retirada e para devolução do veículo, e o grupo do carro que o cliente deseja locar. O período mínimo de locação é de 1 (uma) diária de 24 horas e o período máximo é de 30 diárias. O valor da diária a ser efetivamente praticada será dado pelo valor na data de reserva. Para conduzir o veículo locado, o cliente deverá apresentar Carteira Nacional de Habilitação (CNH) válida e emitida em território nacional. Caso o cliente não preencha o perfil exigido, poderá indicar um condutor habilitado. Em qualquer caso, o cliente pode nomear até quatro motoristas adicionais. Na devolução do veículo, deve-se registrar a data, hora e quilometragem na devolução. Neste momento a locação terá de ser paga. Pagamentos podem ser feitos em dinheiro, cheque ou cartão.

##
1. Tabela "Filiais":
   - Chave Primária: ID_Filial (Tipo de Dados: INT)
   - Nome_Filial (Tipo de Dados: VARCHAR)
   - Endereco (Tipo de Dados: VARCHAR)
   - Telefone (Tipo de Dados: VARCHAR)

2. Tabela "Grupos de Carros":
   - Chave Primária: ID_Grupo (Tipo de Dados: INT)
   - Nome_Grupo (Tipo de Dados: VARCHAR)
   - Valor_Diaria (Tipo de Dados: DECIMAL)

3. Tabela "Modelos de Carros":
   - Chave Primária: ID_Modelo (Tipo de Dados: INT)
   - Nome_Modelo (Tipo de Dados: VARCHAR)

4. Tabela "Carros":
   - Chave Primária: ID_Carro (Tipo de Dados: INT)
   - Chave Estrangeira: ID_Modelo (Referência à Tabela Modelos de Carros)
   - Placa (Tipo de Dados: VARCHAR)
   - Chassi (Tipo de Dados: VARCHAR)
   - RENAVAM (Tipo de Dados: VARCHAR)
   - Ano_Fabricacao (Tipo de Dados: INT)
   - Potencia_Motor (Tipo de Dados: DECIMAL)
   - Cor (Tipo de Dados: VARCHAR)
   - Numero_Portas (Tipo de Dados: INT)

5. Tabela "Equipamentos":
   - Chave Primária: ID_Equipamento (Tipo de Dados: INT)
   - Nome_Equipamento (Tipo de Dados: VARCHAR)

6. Tabela "Clientes":
   - Chave Primária: ID_Cliente (Tipo de Dados: INT)
   - Nome_Cliente (Tipo de Dados: VARCHAR)
   - Tipo_Cliente (Tipo de Dados: VARCHAR)
   - CNH (Tipo de Dados: VARCHAR)

7. Tabela "Reservas":
   - Chave Primária: ID_Reserva (Tipo de Dados: INT)
   - Chave Estrangeira: ID_Cliente (Referência à Tabela Clientes)
   - Chave Estrangeira: ID_Filial_Retirada (Referência à Tabela Filiais)
   - Chave Estrangeira: ID_Filial_Devolucao (Referência à Tabela Filiais)
   - Chave Estrangeira: ID_Grupo_Carro (Referência à Tabela Grupos de Carros)
   - Data_Retirada (Tipo de Dados: DATE)
   - Hora_Retirada (Tipo de Dados: TIME)
   - Data_Devolucao (Tipo de Dados: DATE)
   - Hora_Devolucao (Tipo de Dados: TIME)

8. Tabela "Motoristas_Adicionais" (para armazenar motoristas adicionais em uma reserva):
ESCLARECIMENTO:(
esclarecer o relacionamento "para armazenar motoristas adicionais em uma reserva".

Na tabela "Reservas", você pode armazenar informações sobre uma reserva específica feita por um cliente. No entanto, para acomodar o fato de que um cliente pode indicar motoristas adicionais para dirigir o veículo reservado, você precisará de uma tabela adicional chamada "Motoristas_Adicionais" (ou algo similar) para registrar esses motoristas adicionais.

Aqui está como o relacionamento funciona:

Tabela "Reservas" (Reservas) - Relação "1 para N" com:
Tabela "Motoristas_Adicionais" (Motoristas_Adicionais)
Isso significa que uma única reserva na tabela "Reservas" pode estar associada a vários motoristas adicionais registrados na tabela "Motoristas_Adicionais". Cada entrada na tabela "Motoristas_Adicionais" terá informações sobre um motorista adicional específico nomeado pelo cliente na reserva.

Por exemplo, se um cliente fizer uma reserva e indicar dois motoristas adicionais, você terá uma entrada na tabela "Reservas" relacionada a três entradas na tabela "Motoristas_Adicionais", uma para o cliente principal e uma para cada motorista adicional. Cada entrada na tabela "Motoristas_Adicionais" incluirá informações como o nome do motorista adicional e sua CNH.
)

   - Chave Primária: ID_Motorista_Adicional (Tipo de Dados: INT)
   - Chave Estrangeira: ID_Reserva (Referência à Tabela Reservas)
   - Nome_Motorista (Tipo de Dados: VARCHAR)
   - CNH_Motorista (Tipo de Dados: VARCHAR)

9. Tabela "Devolucoes":
   - Chave Primária: ID_Devolucao (Tipo de Dados: INT)
   - Chave Estrangeira: ID_Reserva (Referência à Tabela Reservas)
   - Data_Devolucao (Tipo de Dados: DATE)
   - Hora_Devolucao (Tipo de Dados: TIME)

Espero que esta lista atenda às suas especificações, incluindo apenas os atributos mencionados no seu cenário original. Certifique-se de configurar as restrições de integridade referencial apropriadas de acordo com a implementação do seu sistema de gerenciamento de banco de dados.









RELAÇÕES
Entendido, vou listar os tipos de relacionamento entre as tabelas, indicando "N para 1" com o nome da entidade correspondente:

1. Tabela "Filiais" (Filiais) - Relação "1 para N" com:
   - Tabela "Carros" (Carros)

2. Tabela "Grupos de Carros" (Grupos) - Relação "1 para N" com:
   - Tabela "Carros" (Carros)

3. Tabela "Modelos de Carros" (Modelos) - Relação "1 para N" com:
   - Tabela "Carros" (Carros)

4. Tabela "Carros" (Carros) - Relação "N para 1" com:
   - Tabela "Grupos de Carros" (Grupos)
   - Tabela "Modelos de Carros" (Modelos)

5. Tabela "Equipamentos" (Equipamentos) - Relação "N para N" com:
   - Tabela "Carros" (Carros) (Relação muitos-para-muitos)

6. Tabela "Clientes" (Clientes) - Relação "1 para N" com:
   - Tabela "Reservas" (Reservas)

7. Tabela "Reservas" (Reservas) - Relação "N para 1" com:
   - Tabela "Clientes" (Clientes)
   - Tabela "Filiais" (Filiais) para Filial de Retirada
   - Tabela "Filiais" (Filiais) para Filial de Devolução
   - Tabela "Grupos de Carros" (Grupos)

8. Tabela "Motoristas_Adicionais" (Motoristas_Adicionais) - Relação "N para 1" com:
   - Tabela "Reservas" (Reservas)

9. Tabela "Devolucoes" (Devolucoes) - Relação "N para 1" com:
   - Tabela "Reservas" (Reservas)

Estas são as relações "N para 1" entre as tabelas com os nomes das entidades correspondentes, de acordo com as informações fornecidas no cenário.




# DSA-Microsoft-Power-BI-Para-Business-Intelligence-e-Data-Science
Projetos realizados durante o curso da Data Science Academy

Este  Mini-Projeto  traz  para  você  uma  breve  introdução  à  análise  de dados de Recursos Humanos com o Power BI. 

O projeto tem como objetivo responder as seguintes perguntas de negócio:

1 - Qual o total de funcionários atualmente na empresa?

TotalFunc = COUNTROWS(DatasetRH)

2 - Qual o tempo médio de experiência dos funcionários (em anos)?

3 - Qual o total e percentual de funcionários do gênero masculino e feminino?

Totais

TotalFeminino = CALCULATE([TotalFunc], DatasetRH[Genero] = "Feminino")

TotalMasculino = CALCULATE([TotalFunc], DatasetRH[Genero] = "Masculino")

Percentuais

% Feminino = DIVIDE([TotalFeminino],[TotalFunc])

% Masculino = DIVIDE([TotalMasculino],[TotalFunc],0)

4 - Qual a média salarial mensal?

SalarioMedio = AVERAGE(DatasetRH[Salario_Mensal])

5 - Qual o total de funcionários por função?

6 - Qual o percentual de funcionários disponíveis para fazer hora extra?

A coluna chamada Disponivel_Hora_Extra está preenchida com dados "S" ou "N". Foi necessário uma transformação usando a função "substituir valores" para mudar os dados para "Sim" e "Não".

7 - Qual o nível de envolvimento dos funcionários no trabalho considerando 4 categorias: Ruim, Baixo, Médio e Alto?

<img width="591" alt="image" src="https://github.com/alearauj/DSA-Microsoft-Power-BI-Para-Business-Intelligence-e-Data-Science/assets/98029951/d46bf702-53bf-4146-ba09-24cc1d7e7769">





8 - Este item não deve estar no Dashboard, mas precisa ser calculado: Qual o total e o percentual de funcionários que devem receber promoção? Considere a coluna “Anos Desde a última Promoção” com a seguinte regra: Se o funcionário tiver 5 anos ou mais desde  a última  promoção,  deve ter  a  promoção  considerada.  Caso  contrário,apromoção não deve ser considerada agora.

= Table.AddColumn(#"Colunas Reordenadas", "promocao", each if [Anos_Desde_Ultima_Promocao] >= 5 then "Considerar promoção" else if [Anos_Desde_Ultima_Promocao] < 5 then "Não considerar promoção" else null)

TotalFuncPromover = CALCULATE([TotalFunc], DatasetRH[promocao] = "Considerar promoção")

TotalFuncNaoPromover = CALCULATE([TotalFunc], DatasetRH[promocao] = "Não considerar promoção")

% Promover = DIVIDE([TotalFuncPromover], [TotalFunc],0)

% NaoPromover = DIVIDE([TotalFuncNaoPromover], [TotalFunc],0)

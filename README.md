![picture](https://s3-sa-east-1.amazonaws.com/shippmedia/general/backend.png)

# Desafio Shipp Front-End

### Fechamento de Pedido de Serviço de Entrega


O teste deve ser feito para Web com layout responsivo. É uma simulação de fechamento de pedido de serviço de entrega utilizando Api do Google.

O usuário deverá escolher os endereços disponibilzados pela api autocomplete do Google para traçar a rota (serão permitidos 'N' pontos de parada), informar a descrição e prosseguir para tela de fechamento de pedido com cartão de credito. Se não houver cartão de credito cadastrado, deverá informá-lo também (número do cartão, data de validade e o CVV) antes de finalizar o pagamento.

Os cartões devem ser persistidos no aplicativo para serem usados em pagamentos futuros.

Devem ser usadas boas práticas de programação, assim como padrões de projeto e Arquitetura.

Documentação Google Places Web: https://developers.google.com/maps/documentation/javascript/places

Documentação Google Places Maps: https://developers.google.com/maps/documentation/javascript/reference/map

Exemplos de uso da Api do Google: https://developers.google.com/maps/documentation/javascript/examples/

O layout está disponível em: https://xd.adobe.com/spec/4dfeb2ae-5f55-4cad-7170-3cd7536d5d2d-3bcf/screen/b95a3d6e-a9f4-4b2c-9ad8-90ba077dce87

-----
###### Resumo do checkout

Para informar os valores do resumo do checkout:  (POST) https://bzevgcar2b.execute-api.sa-east-1.amazonaws.com/evaluate

+ Array de latitude e longitude obitido pela api do google (array [double, double]) 
+ Descrição dos trajetos (string)


REQUEST 

``` json
{  
   "stops": 
   [
   		{
		   "latitude": 23.42,
		   "longitude": 23.12,
		},
		{
		   "latitude": 23.42,
		   "longitude": 23.12,
		}
   ],
   "description": "Bla Bla"
   
}
```

RESPONSE

``` json
{
    "distance": 5.6566,
    "total_value": 90.31,
}
```

-----
###### Fechamento de pedido

Para finalizar o pedido: (POST) https://babkowcbkl.execute-api.sa-east-1.amazonaws.com/service

+ Array de latitude e longitude obitido pelo caminho do google (array [double, double]) 
+ Número do cartão (string)
+ Vencimento do cartão MM/YY (string)
+ CVV (string)
+ Descrição dos trajetos (string)


REQUEST

``` json
{  
   "stops": 
   [
   		{
		   "latitude": 23.42,
		   "longitude": 23.12,
		},
		{
		   "latitude": 23.42,
		   "longitude": 23.12,
		}
   ],
   "card_number":"1111111111111111",
   "cvv":"789",
   "expiry_date":"01/18",
   "description": "Bla Bla"
}
```

RESPONSE

``` json
{  
   "message": "Obrigado por comprar na shipp :D",
   "value":90.31
}
```
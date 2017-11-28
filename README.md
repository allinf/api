# README #

This document describe ALL.INF Customer Relation Platform API functionalities and features. The document is organized in 2 sections:
1) Authentication token and procedure
2) Generic API for request and send data


### Authentication (token) ###

The first step to access ALL.INF API is make an authentication with a valid user. This user will be check with his availability and rules. 
The API URL is https://api.allinf.com.br/apirequest, for this URL a POST over HTTP needs to be sent, as a REST SERVICE (JSON).

Example of authentication request:
[
	{
		"action":"authentication",
		"login":"admin@allinf.com.br",
		"pass":"allinf"
	}
]

API Response:
[
	{
		"api_invalid_token":false,
		"api_status":true,
		"api_data":
			{
				"user_info":
					{
						"is_admin":true,
						"business_unities":
							[
								{
									"legal_id":"24.875.399/0001-12",
									"address":"Praça Silvio Romero, 55 - São Paulo - SP - Brasil",
									"name":"Headquarter",
									"logo":"allinf_logo.png",
									"id":"e8d67e58-f8bf-4011-a9b1-81f923216ddf"
								},
							],
						"password":"202cb962ac59075b964b07152d234b70",
						"selected_business_unity":"",
						"organization_id":"bce94086-51e4-4feb-851b-685dbaf83ef8",
						"active":true,
						"attributes":
							{
								"business_unities":
									[
										"e8d67e58-f8bf-4011-a9b1-81f923216ddf"
									],
								"id_people":"bec89bca-8e19-4be4-9223-c258380ed053"
							},
							"id":"2a228426-e5a1-45ee-8ca9-74e91f750ae7",
							"login":"admin@allinf.com.br",
							"organization_file_server":"https://file.allinf.com.br"
			},
			"user_token":"df8e4f75c7444d3f7a1efd187d239bd9"
		}
	}
]

To send others request to API, the most important information will be the attibute TOKEN, that means authentication process well done.

### Data Request and Upsert ###

To send data (create, edit or delete) and receive data from API, the same endpoint will be invoked, but for each transaction type, will need to change the request payload, as described bellow:
{
  "return": [
    {
      "records_total": 1,
      "callback_key": "first_list_load",
      "records": [
        {
          "main_address_city": "São Paulo",
          "credit_score": 6.6,
          "photo_logo": "IMG_22112017_122305_0.png",
          "main_address_complement": "Cj. 52",
          "main_address_number": "1343",
          "main_address_zip": "01311-200",
          "main_address_long": -46.65476160000003,
          "main_address_district": "Bela Vista",
          "cell_phone": "(11) 98457-0491",
          "main_address_lat": -23.5632322,
          "main_address_state": "SP",
          "full_name": "Bruno Daniel Borges",
          "blocked": false,
          "phone": "(11) 2983-6083",
          "nick_name": "Bruno Borges",
          "main_address": "Av. Paulista, 1343 - Bela Vista, São Paulo - SP, 01311-200, Brasil",
          "credit_limit": 455553.33,
          "freight_type": "NO_FREIGHT",
          "legal_id_1": "32537472802",
          "id": "cae327a0-f63a-4ddf-bda5-084a46fc8c33",
          "email": "bruno.borges@allinf.com.br"
        }
      ],
      "records_amount": 1,
      "api_status": true,
      "source_request_parameter": "DataAccess",
      "current_page": 1,
      "records_per_request": 50
    }
  ]
}

This document, as a representation of source OBJECT inside ALL.INF plataform (examples: customers, products, tickets, etc).

Expressões Regulares:
	Explicações:
		pattern: expressão regular, é a regra que diz o que deve ser buscado;
		
		target string: é a string alvo onde vai ser feita a busca pela string que satisfaz a pattern;
		
		match: é o resultado da busca;
		
		meta-chars: são caracteres que não são interpretados literalmente pelo regex engine, ou seja, se colocarmos ele na pattern, ele não será buscado pelo seu real valor.
		OBS: Caso deseja que o regex engine encontre o valor verdadeiro do caractere, é preciso adicionar um "\" antes do caractere desejado. Exemplo: "\.", vai buscar o ".";
		
		quantifiers: Servem para dizer quantas vezes o caractere alvo vai se repetir, é representado por um numero inteiro entre chaves:
			exemplo de quantifier: \d{3} = vai buscar 3 dígitos em sequência (um do lado do outro);
		
		classes de caracteres: Servem para buscar um conjunto de caracteres desejados, sempre são representados dentro de "[]", exemplos: "[-.]", vai buscar onde exista um "-" ou um ".";
		OBS: quando aplicados dentro das classes de caracteres, os meta-chars deixam de ser meta-chars e se tornam caracteres normais, logo, quando se deseja busca um "." utilizando classes de caracteres, ficaria assim: "[.]";

	Dicas / atalhos:
		"\d": é a mesma coisa que o "[0123456789]" e o "[0-9]", todos buscam números de 0 a 9;
		"\s": serve para buscar espaços em branco (whitespaces, espaços, tabs, etc...);
		"+": serve para buscar 1 ou mais vezes, quando não sabemos quantas vezes ele pode aparecer;
		"?": serve para buscar 0 ou 1 vez;
		"*": serve para buscar 0 ou mais vezes;
		"{n}": serve para buscar exatemente n vezes (n é um número definido);
		"{n,}": serve para buscar no mínimo n vezes;
		"{n,m}": serve para buscar no mínimo n+1 vezes, no máximo m vezes;
		"\w": significa word char e é um atalho para [A-Za-z0-9_];
		
	Exercícios:
		1) Buscar todos os números de 1 dígito na string:
			target string: "João Fulano,123.456.789-00,21 de Maio de 1993,(21) 3079-9987,Rua do Ouvidor,50,20040-030,Rio de Janeiro";
			pattern: "\d";
			match: "1|2|3|4|5|6|7|8|9|0|0|2|1|1|9|9|3|2|1|3|0|7|9|9|9|8|7|5|0|2|0|0|4|0|0|3|0";
		
		2) Buscar números de 3 dígitos na string:
			target string: "João Fulano,123.456.789-00,21 de Maio de 1993,(21) 3079-9987,Rua do Ouvidor,50,20040-030,Rio de Janeiro";
			pattern: "\d\d\d";
			match: "123|456|789|199|307|998|200|030";
			
		3) Buscar números de 3 dígitos com um ponto no final:
			target string: "João Fulano,123.456.789-00,21 de Maio de 1993,(21) 3079-9987,Rua do Ouvidor,50,20040-030,Rio de Janeiro";
			pattern: "\d\d\d\.";
			match: "123.|456.";
			
		4) Buscar os 2 primeiros blocos do CPF:
			target string: "João Fulano,123.456.789-00,21 de Maio de 1993,(21) 3079-9987,Rua do Ouvidor,50,20040-030,Rio de Janeiro";
			pattern: "\d\d\d\.\d\d\d\.";
			match: "123.456.";
			
		5) Buscar os 3 primeiros blocos do CPF:
			target string: "João Fulano,123.456.789-00,21 de Maio de 1993,(21) 3079-9987,Rua do Ouvidor,50,20040-030,Rio de Janeiro";
			pattern: "\d\d\d\.\d\d\d\.\d\d\d";
			match: "123.456.789";
			
		6) Buscar os 3 primeiros blocos do CPF com o "-":
			target string: "João Fulano,123.456.789-00,21 de Maio de 1993,(21) 3079-9987,Rua do Ouvidor,50,20040-030,Rio de Janeiro";
			pattern: "\d\d\d\.\d\d\d\.\d\d\d-";
			match: "123.456.789-";
			
		7) Buscar o CPF completo:
			target string: "João Fulano,123.456.789-00,21 de Maio de 1993,(21) 3079-9987,Rua do Ouvidor,50,20040-030,Rio de Janeiro";
			pattern: "\d\d\d\.\d\d\d\.\d\d\d-\d\d";
			match: "123.456.789-00";
			
		8) Buscar o CPF completo, porém com a pattern simplificada utilizando quantifiers:
			target string: "João Fulano,123.456.789-00,21 de Maio de 1993,(21) 3079-9987,Rua do Ouvidor,50,20040-030,Rio de Janeiro";
			pattern: "\d{3}\.\d{3}\.\d{3}-\d{2}";
			match: "123.456.789-00";
			
		9) Buscar um CNPJ:
			target string: "Baseado no que aprendemos, defina a expressão regular para encontrar um CNPJ, por exemplo: 15.123.321/8883-22";
			pattern: "\d{2}\.\d{3}\.\d{3}\/\d{4}-\d{2}";
			match: "15.123.321/8883-22";
			
		10) Buscar diferentes endereços de IP:
			target string: "Baseado no que aprendemos, defina a expressão regular para encontrar um CNPJ, por exemplo: 126.1.112.34, 128.126.12.244, 192.168.0.34"
            pattern: "\d{3}\.\d{1,3}\.\d{1,3}\.\d{1,3}";
            match: "126.1.112.34|128.126.12.244|192.168.0.34";
			
		11) Buscar o CEP:
			target string: "João Fulano,123.456.789-00,21 de Maio de 1993,(21) 3079-9987,Rua do Ouvidor,50,20040-030,Rio de Janeiro";
            pattern: "\d{5}-\d{3}";
            match: "20040-030";
		
		12) Buscar o número de telefone, tanto com o 9 na frente, quanto sem:
			target string: "encontrar o número telefônico? Por exemplo: (21) 3216-2345, (21) 93216-2345";
			pattern: "\(\d{2}\) \d{4,5}-\d{4}";
			match: "(21) 3216-2345|(21) 93216-2345";
		
		13) Buscar o CPF completo, com pontuação ou não:
			target string: "João Fulano,123.456.789-00,21 de Maio de 1993,(21) 3079-9987,Rua do Ouvidor,50,20040-030,Rio de Janeiro. Maria Fulana, 98765432100,11 de Abril de 1995,(11) 933339871,Rua Vergueiro,3185,04101-300,São Paulo";
			pattern: "\d{3}\.?\d{3}\.?\d{3}-?\d{2}";
			match: "123.456.789-00|98765432100";
		
		14) Buscar o CPF completo, com ponto, hifen, ou só os números:
			target string: "João Fulano,123.456.789-00,21 de Maio de 1993,(21) 3079-9987,Rua do Ouvidor,50,20040-030,Rio de Janeiro. Maria Fulana, 98765432100,11 de Abril de 1995,(11) 933339871,Rua Vergueiro,3185,04101-300,São Paulo. denise teste, 987.654.321.00,28 de Dezembro de 1991,(31)45562712,SCS Qd. 8 Bl. B-50,11,70333-900,Rio Grande";
			pattern: "\d{3}\.?\d{3}\.?\d{3}[-.]?\d{2}";
			match: "123.456.789-00|98765432100|987.654.321.00";
		
		15) Buscar a tag <code> ou <\code> dentro da string:
			target string: "No <code>for</code>, o valor de <code>i</code> começa de zero e é incrementado a cada volta enquanto <code>i < 10</code>, portando o bloco de código do for é executado 10 vezes.";
			pattern: "</?code>";
			match: "<code>|</code>|<code>|</code>|<code>|</code>";
		
		16) Buscar os números entre 1 e 3 e os números entre 5 e 7:
			target string: "teste 123456789";
			pattern: "[1-35-7]";
			match: "1|2|3|5|6|7";
		
		17) Buscar a data por extenso:
			target string: "João Fulano,123.456.789-00,21     de Março de 1993,(21) 3079-9987,Rua do Ouvidor,50,20040-030,Rio de Janeiro";
			pattern: "[1-3]?\d\s+de\s+[jfmasond,JFMASOND][A-ZÇ,a-zç]+\s+de\s+\d{4}";
			match: "21     de Dezembro de 1993";
		
		18) Buscar um horário definido como "19h32min16s":
			target string: "Agora precisamos garantir que o nosso usuário preencha um horário que siga esse padrão: 19h32min16s.";
			pattern: "\d{2}h\d{2}min\d{2}s";
			match: "19h32min16s";
		
		19) Buscar placas de carros (formato antigo), com traço ou não:
			target string: "Exemplo de placa: KMG-8089";
			patter: "[A-Z]{3}-?\d{4}";
			match: "";
		
		20) Buscar placas de carros (tanto no formato antigo quanto no novo), com traço ou não
			target string: "Exemplo de placa: KMG-8G89";
			pattern: "[A-Z]{3}-?\d[0-9,A-Z]\d{2}";
			match: "KMG-8G89";
		
		21) Buscar a nota e os nomes dos alunos que tiraram notas entre 7.2 e 7.9:
			target string: "9.8 - Robson, 7.1 - Teresa, 4.5 - Armênio, 6.5 - Zulu, 7.7 - Stefania, 7.8 - João, 5.0 - Romeu, 7.2 - Pompilho, 3.1 - Reinaldo, 7.3 - Bernadete, 4.7 - Cinério ";
			pattern: "7\.[2-9]\s+-\s+[A-ZÀ-Ú][a-zà-ú]+";
			match: "7.7 - Stefania | 7.8 - João | 7.2 - Pompilho | 7.3 - Bernadete";
		
		22) Buscar a nota e o nome dos alunos que precisam de meio ponto ou menos para atingir a nota 8:
			target string: "10 - Bruce, 9.5 - Miranda, 7.9    - Bob, 10 - Zimbabue, 7.5 - Bety"
			pattern: "7\.[5-9]\s+-\s+[A-ZÀ-Ú][a-zà-ú]+"
			match: "7.9    - Bob | 7.5 - Bety"
		
		23) Buscar as palavras GARROTE, SERROTE e ROTEIRO:
			target string: "BALEIRO GARROTE SERROTE GOLEIRO ROTEIRO "
			pattern: "[A-Z]*ROT[A-Z]*"
			match: "GARROTE | SERROTE | ROTEIRO"
		
		24) Buscar "?classes+poderosas*":
			target string: "?classes+poderosas*";
			pattern: "[a-z?*+]+";
			match: "?classes+poderosas*";
			
		25) Validar um username de usuário com as seguintes validações:
			1) o limite é de 10 caracteres;
			2) o primeiro caractere deve ser uma letra do alfabeto (tanto minúscula quanto maiúscula), não pode ser um número;
			3) a partir do segundo caractere podemos ter letras (tanto minúscula quanto maiúscula) e números.
			
			target string: "A8am90818t";
			pattern: "[a-zA-Z][a-zA-Z0-9]{0,9}";
			match: "A8am90818t";
		
		
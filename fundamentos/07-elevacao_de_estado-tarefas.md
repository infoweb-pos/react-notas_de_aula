# Compartilhando estado entre componentes com elevação de estado (lifiting state) - uma lista de tarefas
- **Tema**: Fundamentos de React
- **Subtema**: Fundamentos - Compartilhar estado entre componentes com elevação de estado
- **código-fonte**: [github](https://github.com/infoweb-pos/07-02-elevacao_de_estado-tarefas) [zip](https://github.com/infoweb-pos/07-02-elevacao_de_estado-tarefas/archive/refs/tags/2023.zip)

## Objetivos
- Criar componentes que compartilham estado do componente pai

## Resumo
Será criado um projeto javascript de uma aplicação web com o framework React e a 
linguagem de programação TypeScript usando o aplicativo npm e o script vite.
O aplicativo web será encapsulado no componente React `App` que conterá um título, 
uma entrada de texto e uma lista de itens. 
Todos encapsulados por componentes React da aplicação.

## Sumário
1. [Criar o projeto e limpar o código](https://github.com/infoweb-pos/react-notas_de_aula/blob/main/fundamentos/07-elevacao_de_estado-tarefas.md#1-criar-o-projeto-e-limpar-o-c%C3%B3digo)
2. [Criar o componente `AppNavBar` com o título da aplicação e adicionar instância em `App`](https://github.com/infoweb-pos/react-notas_de_aula/blob/main/fundamentos/07-elevacao_de_estado-tarefas.md#2-criar-o-componente-appnavbar-com-o-t%C3%ADtulo-da-aplica%C3%A7%C3%A3o-e-adicionar-inst%C3%A2ncia-em-app)
3. [Criar o componente `AppTarefaEditar` com o título da aplicação e adicionar instância em `App`](https://github.com/infoweb-pos/react-notas_de_aula/blob/main/fundamentos/07-elevacao_de_estado-tarefas.md#3-criar-o-componente-apptarefaeditar-com-o-t%C3%ADtulo-da-aplica%C3%A7%C3%A3o-e-adicionar-inst%C3%A2ncia-em-app)
4. [Criar o componente `AppTarefaLista` com o título da aplicação e adicionar instância em `App`](https://github.com/infoweb-pos/react-notas_de_aula/blob/main/fundamentos/07-elevacao_de_estado-tarefas.md#4-criar-o-componente-apptarefalista-com-o-t%C3%ADtulo-da-aplica%C3%A7%C3%A3o-e-adicionar-inst%C3%A2ncia-em-app)
5. [Transferir os dados do HTML do componente `AppTarefaLista` para variáveis](https://github.com/infoweb-pos/react-notas_de_aula/blob/main/fundamentos/07-elevacao_de_estado-tarefas.md#5-transferir-os-dados-do-html-do-componente-apptarefalista-para-vari%C3%A1veis)
6. [Criar estado para o componente `AppTarefaEditar` com valor inicial](https://github.com/infoweb-pos/react-notas_de_aula/blob/main/fundamentos/07-elevacao_de_estado-tarefas.md#6-criar-estado-para-o-componente-apptarefaeditar-com-valor-inicial)
7. [Criar estado para o componente `AppTarefaLista` com valor inicial](https://github.com/infoweb-pos/react-notas_de_aula/blob/main/fundamentos/07-elevacao_de_estado-tarefas.md#7-criar-estado-para-o-componente-apptarefalista-com-valor-inicial)
8. [Elevar o estado do componente `AppTarefaLista` para `App`](https://github.com/infoweb-pos/react-notas_de_aula/blob/main/fundamentos/07-elevacao_de_estado-tarefas.md#8-elevar-o-estado-do-componente-apptarefalista-para-app)
9. [Elevar o estado do componente `AppTarefaEditar` para `App`](https://github.com/infoweb-pos/react-notas_de_aula/blob/main/fundamentos/07-elevacao_de_estado-tarefas.md#9-elevar-o-estado-do-componente-apptarefaeditar-para-app)
10. [Criar função para adicionar novas tarefas](https://github.com/infoweb-pos/react-notas_de_aula/blob/main/fundamentos/07-elevacao_de_estado-tarefas.md#10-criar-fun%C3%A7%C3%A3o-para-adicionar-novas-tarefas)

### 1. Criar o projeto e limpar o código
1. Abrir o terninal de comandos
2. Criar projeto novo com React e TypeScript
3. Entrar no diretório do projeto, instalar bibliotecas e executar aplicativo
4. Executar o visual studio code e abrir diretório do projeto
5. Editar o arquivo `src/App.tsx`
6. Abrir o navegador e acessar a url http://localhost:5173/

**terminal de comandos**
```console
$ npm create vite@latest
✔ Project name: … 07-02-elevacao_de_estado-tarefas
✔ Select a framework: › React
✔ Select a variant: › TypeScript

Scaffolding project in /home/minora/minora/2023-pos/07-02-elevacao_de_estado-tarefas...

Done. Now run:

  cd 07-02-elevacao_de_estado-tarefas
  npm install
  npm run dev

$ cd 07-02-elevacao_de_estado-tarefas

[07-02-elevacao_de_estado-tarefas] $ npm install
added 209 packages, and audited 210 packages in 15s

39 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities

[07-02-elevacao_de_estado-tarefas] $ npm run dev
 VITE v4.3.9  ready in 400 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
  ➜  press h to show help

```

**arquivo** `src/App.tsx`
```javascript
import './App.css'

const App = () => {

  return (
    <>
    </>
  )
}

export default App

```

### 2. Criar o componente `AppNavBar` com o título da aplicação e adicionar instância em `App`
1. Criar uma constante para o componente `AppNavBar`
2. Adicioanar uma instância do componente `AppNavBar` em `App`

**arquivo** `src/App.tsx`
```javascript
import "./App.css";

const AppNavBar = () => {
	return (
		<div className="card">
			<h1>Lista de tarefas</h1>
		</div>
	);
};

const App = () => {
	return (
		<>
			<AppNavBar />
		</>
	);
};

export default App;

```

### 3. Criar o componente `AppTarefaEditar` com o título da aplicação e adicionar instância em `App`
1. Criar uma constante para o componente `AppTarefaEditar`
2. Adicioanar uma instância do componente `AppTarefaEditar` em `App`

**arquivo** `src/App.tsx`
```javascript
import "./App.css";

const AppNavBar = () => {
	return (
		<div className="card">
			<h1>Lista de tarefas</h1>
		</div>
	);
};

const AppTarefaEditar = () => {
  return (
    <div className="card">
      <label>Tarefa: </label>
      <input type="text" />
      <button>Adicionar</button>
    </div>
  );
}

const App = () => {
	return (
		<>
			<AppNavBar />
      <AppTarefaEditar />
		</>
	);
};

export default App;

```

### 4. Criar o componente `AppTarefaLista` com o título da aplicação e adicionar instância em `App`
1. Criar uma constante para o componente `AppTarefaLista`
2. Adicioanar uma instância do componente `AppTarefaLista` em `App`

**arquivo** `src/App.tsx`
```javascript
import "./App.css";

const AppNavBar = () => {
	return (
		<div className="card">
			<h1>Lista de tarefas</h1>
		</div>
	);
};

const AppTarefaEditar = () => {
  return (
    <div className="card">
      <label>Tarefa: </label>
      <input type="text" />
      <button>Adicionar</button>
    </div>
  );
}

const AppTarefaLista = () => {
  return (
    <div className="card">
      <ul>
        <li>Prototipar interface do usuário</li>
        <li>Implementar com HTML a interface com o usário em React</li>
        <li>Extrair componentes React da implementação HTML</li>
        <li>Transferir os dados do HTML dos componentes React para variáveis</li>
        <li>Modificar os dados de variáveis para estado ou propriedades de componentes</li>
        <li>Elevar os estados dos componentes quando tiver dados compartilhados</li>
        <li>Programar a modificação dos estados</li>
      </ul>
    </div>
  )
}

const App = () => {
	return (
		<>
			<AppNavBar />
      <AppTarefaEditar />
      <AppTarefaLista />
		</>
	);
};

export default App;

```

### 5. Transferir os dados do HTML do componente `AppTarefaLista` para variáveis
1. Criar constante `tarefas`
2. Transferir os dados do HTML em `li` para strings em `tarefas`
3. Substituir os `li` do HTML em `tarefas.map`

**arquivo** `src/App.tsx`
```javascript
import "./App.css";

const AppNavBar = () => {
	return (
		<div className="card">
			<h1>Lista de tarefas</h1>
		</div>
	);
};

const AppTarefaEditar = () => {
	return (
		<div className="card">
			<label>Tarefa: </label>
			<input type="text" />
			<button>Adicionar</button>
		</div>
	);
};

const AppTarefaLista = () => {
	const tarefas = [
		"Prototipar interface do usuário",
		"Implementar com HTML a interface com o usário em React",
		"Extrair componentes React da implementação HTML",
		"Transferir os dados do HTML dos componentes React para variáveis",
		"Modificar os dados de variáveis para estado ou propriedades de componentes",
		"Elevar os estados dos componentes quando tiver dados compartilhados",
		"Programar a modificação dos estados",
	];
	return (
		<div className="card">
			<ul>
				{tarefas.map((item, index) => (
					<li key={index}>{item}</li>
				))}
			</ul>
		</div>
	);
};

const App = () => {
	return (
		<>
			<AppNavBar />
			<AppTarefaEditar />
			<AppTarefaLista />
		</>
	);
};

export default App;

```

### 6. Criar estado para o componente `AppTarefaEditar` com valor inicial
1. criar o estado `tarefa` no componente `AppTarefaEditar` colocando como valor inicial uma string vazia.
2. adicionar o estado `tarefa` no `input` do componente `AppTarefaEditar`. obs: você irá digitar e não irá mudar nada na caixa de texto.
3. adicionar o evento `onChange` no `input` do componente `AppTarefaEditar`.

**arquivo** `src/App.tsx`
```javascript
import { useState } from "react";
import "./App.css";

const AppNavBar = () => {
	return (
		<div className="card">
			<h1>Lista de tarefas</h1>
		</div>
	);
};

const AppTarefaEditar = () => {
	const [tarefa, setTarefa] = useState("");

	return (
		<div className="card">
			<label>Tarefa: </label>
			<input
				type="text"
				value={tarefa}
				onChange={(e: React.FormEvent<HTMLInputElement>) =>
					setTarefa(e.target.value)
				}
			/>
			<button>Adicionar</button>
		</div>
	);
};

const AppTarefaLista = () => {
	const tarefas = [
		"Prototipar interface do usuário",
		"Implementar com HTML a interface com o usário em React",
		"Extrair componentes React da implementação HTML",
		"Transferir os dados do HTML dos componentes React para variáveis",
		"Modificar os dados de variáveis para estado ou propriedades de componentes",
		"Elevar os estados dos componentes quando tiver dados compartilhados",
		"Programar a modificação dos estados",
	];
	return (
		<div className="card">
			<ul>
				{tarefas.map((item, index) => (
					<li key={index}>{item}</li>
				))}
			</ul>
		</div>
	);
};

const App = () => {
	return (
		<>
			<AppNavBar />
			<AppTarefaEditar />
			<AppTarefaLista />
		</>
	);
};

export default App;

```

### 7. Criar estado para o componente `AppTarefaLista` com valor inicial
1. modificar a constante `tarefas` para estado no componente `AppTarefaLista` colocando como valor inicial lista de string.

**arquivo** `src/App.tsx`
```javascript
import { useState } from "react";
import "./App.css";

const AppNavBar = () => {
	return (
		<div className="card">
			<h1>Lista de tarefas</h1>
		</div>
	);
};

const AppTarefaEditar = () => {
	const [tarefa, setTarefa] = useState("");

	return (
		<div className="card">
			<label>Tarefa: </label>
			<input
				type="text"
				value={tarefa}
				onChange={(e: React.FormEvent<HTMLInputElement>) =>
					setTarefa(e.target.value)
				}
			/>
			<button>Adicionar</button>
		</div>
	);
};

const AppTarefaLista = () => {
	const [tarefas, setTarefas] = useState([
		"Prototipar interface do usuário",
		"Implementar com HTML a interface com o usário em React",
		"Extrair componentes React da implementação HTML",
		"Transferir os dados do HTML dos componentes React para variáveis",
		"Modificar os dados de variáveis para estado ou propriedades de componentes",
		"Elevar os estados dos componentes quando tiver dados compartilhados",
		"Programar a modificação dos estados",
	]);
  
	return (
		<div className="card">
			<ul>
				{tarefas.map((item, index) => (
					<li key={index}>{item}</li>
				))}
			</ul>
		</div>
	);
};

const App = () => {
	return (
		<>
			<AppNavBar />
			<AppTarefaEditar />
			<AppTarefaLista />
		</>
	);
};

export default App;

```

### 8. Elevar o estado do componente `AppTarefaLista` para `App`
1. Copiar o estado do componente `AppTarefaLista` para `App`;
2. Adicionar o parâmetro `props: any` ao componente `AppTarefaLista`;
3. Adicionar a propriedade `data={tarefas}` na instância `AppTarefaLista` em `App`
4. Substituir no componente `AppTarefaLista` de `tarefas.map` por `props.data.map`;
5. Apagar o estado local `tarefas` do componente `AppTarefaLista`.

**arquivo** `src/App.tsx`
```javascript
import { useState } from "react";
import "./App.css";

const AppNavBar = () => {
	return (
		<div className="card">
			<h1>Lista de tarefas</h1>
		</div>
	);
};

const AppTarefaEditar = () => {
	const [tarefa, setTarefa] = useState("");

	return (
		<div className="card">
			<label>Tarefa: </label>
			<input
				type="text"
				value={tarefa}
				onChange={(e: any) => setTarefa(e.target.value)}
			/>
			<button>Adicionar</button>
		</div>
	);
};

const AppTarefaLista = (props: any) => {
	return (
		<div className="card">
			<ul>
				{props.data.map((item: string, indice: number) => (
					<li key={indice}>{item}</li>
				))}
			</ul>
		</div>
	);
};

const App = () => {
	const [tarefas, setTarefas] = useState([
		"Prototipar interface do usuário",
		"Implementar com HTML a interface com o usário em React",
		"Extrair componentes React da implementação HTML",
		"Transferir os dados do HTML dos componentes React para variáveis",
		"Modificar os dados de variáveis para estado ou propriedades de componentes",
		"Elevar os estados dos componentes quando tiver dados compartilhados",
		"Programar a modificação dos estados",
	]);

	return (
		<>
			<AppNavBar />
			<AppTarefaEditar />
			<AppTarefaLista data={tarefas} />
		</>
	);
};

export default App;

```

### 9. Elevar o estado do componente `AppTarefaEditar` para `App`
1. Copiar a função anônima de `onChange` para uma constante `tratarMudanca`;
2. Copiar o estado `tarefa` do componente `AppTarefaEditar` para `App`;
3. Copiar a constante `tratarMudanca` do componente `AppTarefaEditar` para `App` como `tratarMudancaTexto`;
4. Adicionar o parâmetro `props: any` ao componente `AppTarefaEditar`;
5. Adicionar a propriedade `valor={tarefa}` e `mudar={tratarMudancaTexto}` na instância `AppTarefaLista` em `App`
6. Substituir no componente `AppTarefaEditar` de `value={tarefa}` por `value={props.valor}`;
7. Substituir no componente `AppTarefaEditar` de `onChange={tratarMudanca}` por `onChange={props.mudar}`;
8. Apagar o estado local `tarefa` e a função `tratarMudanca` do componente `AppTarefaEditar`.

```javascript
import { useState } from "react";
import "./App.css";

const AppNavBar = () => {
	return (
		<div className="card">
			<h1>Lista de tarefas</h1>
		</div>
	);
};

const AppTarefaEditar = (props: any) => {
	return (
		<div className="card">
			<label>Tarefa: </label>
			<input type="text" value={props.valor} onChange={props.mudar} />
			<button>Adicionar</button>
		</div>
	);
};

const AppTarefaLista = (props: any) => {
	return (
		<div className="card">
			<ul>
				{props.data.map((item: string, indice: number) => (
					<li key={indice}>{item}</li>
				))}
			</ul>
		</div>
	);
};

const App = () => {
	const [tarefa, setTarefa] = useState("");
	const tratarMudancaTexto = (e: any) => setTarefa(e.target.value);
	const [tarefas, setTarefas] = useState([
		"Prototipar interface do usuário",
		"Implementar com HTML a interface com o usário em React",
		"Extrair componentes React da implementação HTML",
		"Transferir os dados do HTML dos componentes React para variáveis",
		"Modificar os dados de variáveis para estado ou propriedades de componentes",
		"Elevar os estados dos componentes quando tiver dados compartilhados",
		"Programar a modificação dos estados",
	]);

	return (
		<>
			<AppNavBar />
			<AppTarefaEditar
				valor={tarefa}
				mudar={tratarMudancaTexto}
			/>
			<AppTarefaLista data={tarefas} />
		</>
	);
};

export default App;

```

### 10. Criar função para adicionar novas tarefas
1. Criar a função `tarefaAdicionar` para adicionar o valor do estado `tarefa` na lista do estado `tarefas` em `App`;
2. Adicionar a propriedade `adicionar` na instância do componente `AppTarefaEditar` em `App`;
3. Adicionar o evento `onClick={props.adicionar}` no botão em `AppTarefaEditar`.

```javascript
import { useState } from "react";
import "./App.css";

const AppNavBar = () => {
	return (
		<div className="card">
			<h1>Lista de tarefas</h1>
		</div>
	);
};

const AppTarefaEditar = (props: any) => {
	return (
		<div className="card">
			<label>Tarefa: </label>
			<input type="text" value={props.valor} onChange={props.mudar} />
			<button onClick={props.adicionar}>Adicionar</button>
		</div>
	);
};

const AppTarefaLista = (props: any) => {
	return (
		<div className="card">
			<ul>
				{props.data.map((item: string, indice: number) => (
					<li key={indice}>{item}</li>
				))}
			</ul>
		</div>
	);
};

const App = () => {
	const [tarefa, setTarefa] = useState("");
	const tratarMudancaTexto = (e: any) => setTarefa(e.target.value);
	const [tarefas, setTarefas] = useState([
		"Prototipar interface do usuário",
		"Implementar com HTML a interface com o usário em React",
		"Extrair componentes React da implementação HTML",
		"Transferir os dados do HTML dos componentes React para variáveis",
		"Modificar os dados de variáveis para estado ou propriedades de componentes",
		"Elevar os estados dos componentes quando tiver dados compartilhados",
		"Programar a modificação dos estados",
	]);
	const tarefaAdicionar = () => {
		const lista = tarefas;
		lista.push(tarefa);
		setTarefas(lista);
		setTarefa("");
	};

	return (
		<>
			<AppNavBar />
			<AppTarefaEditar
				valor={tarefa}
				mudar={tratarMudancaTexto}
				adicionar={tarefaAdicionar}
			/>
			<AppTarefaLista data={tarefas} />
		</>
	);
};

export default App;

```

## Links
- React
  - Learn React
    - [Quick start - Sharing data between components](https://react.dev/learn#sharing-data-between-components)
    - [Sharing State Between Components](https://react.dev/learn/sharing-state-between-components)
  - Aprendendo React
    - [Elevando o State](https://pt-br.legacy.reactjs.org/docs/lifting-stahttps://github.com/infoweb-pos/react-notas_de_aula/blob/main/fundamentos/07-elevacao_de_estado-tarefas.md#10-criar-fun%C3%A7%C3%A3o-para-adicionar-novas-tarefaste-up.html)
- MDN (Mozilla Developer Network) Eventos
  - PT-BR https://developer.mozilla.org/pt-BR/docs/Web/API/Element/click_event
  - EN https://developer.mozilla.org/en-US/docs/Web/API/Element/click_event
 

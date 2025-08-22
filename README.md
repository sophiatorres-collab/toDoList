 var listaTarefas = []
 var listaConcluidas = []

function carregaInformacoes() { 


    document.getElementById("numTarefas").innerHTML = listaTarefas.length 

    document.getElementById("numConcluidas").innerHTML = listaConcluidas.length 


    if (listaTarefas.length === 0) {
        document.getElementById("semTarefas").style.display = "flex"
        document.getElementById("listaTarefas").style.display = "none"
    } else {
        document.getElementById("semTarefas").style.display = "none"
        document.getElementById("listaTarefas").style.display = "flex"    
    }    
} 

function listaTodasTarefas() {
    var htmllistaTarefas = document.getElementById("listaTarefas")
    htmllistaTarefas.innerHTML = ""

    listaTarefas.forEach(function(item, index)  {
        htmllistaTarefas.innerHTML += `           
         <div class="tarefa">
                <button onclick="concluirTarefa(${index})" class="btnConcluir" title="Concluir Tarefa"><title>Concluir Tarefa</title></button>
                <p>${item} </p>
                <button onclick="excluirTarefa(${index})" title="Excluir Tarefa"> <img src="./assets/img/lixeira.png" alt="Icone lixeira"></button>
        </div>` 
    })


     listaConcluidas.forEach(function(item, index)  {
        htmllistaTarefas.innerHTML += `           
         <div class="done">
                <button onclick="concluirTarefa(${index})" class="btnConcluir" title="Concluir Tarefa"><title>Concluir Tarefa</title></button>
                <p>${item} </p>
                <button onclick="excluirTarefa(${index})" title="Excluir Tarefa"> <img src="./assets/img/lixeira.png" alt="Icone lixeira"></button>
        </div>` 
    })    // listar tarefas já concluidas
}
    
//  conclui
function concluirTarefa(index){
    listaConcluidas.push(listaTarefas[index])   
    listaTarefas.splice(index, 1)
                  

    carregaInformacoes()
    listaTodasTarefas()
}


function excluirTarefa (index){
    listaTarefas.splice(index, 1)  
    carregaInformacoes()
    listaTodasTarefas()
}

carregaInformacoes()
listaTodasTarefas()


var formCadastro = document.getElementById("formCadastroTarefa")

formCadastro.addEventListener("submit", function (event){
    event.preventDefault(); 
    
    var form = new FormData(this);

    var tarefa = form.get("tarefa")

    listaTarefas.push(tarefa)

    carregaInformacoes()
    listaTodasTarefas()

})



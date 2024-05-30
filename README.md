# Desafio Dio -  Script para criar um jogo de obstáculos no Roblox****



**Programa:** Roblox Studio

**Código:** Lua

**Script para criar um jogo de obstáculos no Roblox:**

lua



```lua
-- Variáveis globais
local jogadores = {} -- Tabela para armazenar os jogadores no jogo
local obstaculos = {} -- Tabela para armazenar os obstáculos no jogo
local velocidadeDoJogador = 10 -- A velocidade do jogador
local velocidadeDoObstaculo = 5 -- A velocidade do obstáculo

-- Função para criar um novo jogador
function criarJogador(nome)
    local novoJogador = Instance.new("Player")
    novoJogador.Name = nome
    novoJogador.Parent = game.Workspace
    table.insert(jogadores, novoJogador)
end

-- Função para criar um novo obstáculo
function criarObstaculo()
    local novoObstaculo = Instance.new("Part")
    novoObstaculo.Size = Vector3.new(1, 1, 1)
    novoObstaculo.Color = Color3.new(1, 0, 0)
    novoObstaculo.Position = Vector3.new(math.random(-10, 10), 10, math.random(-10, 10))
    novoObstaculo.Parent = game.Workspace
    table.insert(obstaculos, novoObstaculo)
end

-- Função para atualizar o jogo
function atualizarJogo(dt)
    -- Atualiza a posição do jogador
    for i, jogador in pairs(jogadores) do
        local direcao = jogador.Head:GetUnitRay().Direction
        jogador.Position = jogador.Position + direcao * velocidadeDoJogador * dt
    end

    -- Atualiza a posição dos obstáculos
    for i, obstaculo in pairs(obstaculos) do
        obstaculo.Position = obstaculo.Position + Vector3.new(0, -velocidadeDoObstaculo * dt, 0)
    end

    -- Verifica se algum jogador colidiu com algum obstáculo
    for i, jogador in pairs(jogadores) do
        for j, obstaculo in pairs(obstaculos) do
            if jogador:GetTouchingParts()[obstaculo] then
                -- O jogador colidiu com um obstáculo, então remove o jogador do jogo
                jogador:Destroy()
                table.remove(jogadores, i)
            end
        end
    end

    -- Cria novos obstáculos aleatoriamente
    if math.random() < 0.01 then
        criarObstaculo()
    end
end

-- Função para desenhar o jogo
function desenharJogo()

end

-- Evento para quando um novo jogador entra no jogo
game.Players.PlayerAdded:Connect(function(jogador)
    criarJogador(jogador.Name)
end)

-- Evento para quando o jogo é atualizado
game:GetService("RunService").RenderStepped:Connect(atualizarJogo)

-- Evento para quando o jogo é desenhado
game:GetService("RunService").RenderStepped:Connect(desenharJogo)
```



#### **Observações:**

- Você precisará criar um novo jogo no Roblox Studio para usar este script.
- Você pode personalizar o script para criar seu próprio jogo de obstáculos exclusivo.
- Você pode adicionar recursos adicionais ao jogo, como power-ups e diferentes tipos de obstáculos.

Este script criará um jogo de obstáculos básico no Roblox. O jogo contará com jogadores que tentam evitar obstáculos enquanto correm para a linha de chegada. O jogo será atualizado e desenhado em tempo real.

```python
import bpy
import roblox

# Caminho para o arquivo do modelo 3D
model_path = "caminho/para/o/modelo.fbx"

# Importa o modelo para o Blender
bpy.ops.import_scene.fbx(filepath=model_path)

# Obtém o objeto do modelo
model_object = bpy.context.selected_objects[0]

# Cria um novo material para o modelo
material = bpy.data.materials.new(name="Material do modelo")

# Define a cor do material
material.diffuse_color = (1, 0, 0)

# Atribui o material ao modelo
model_object.data.materials.append(material)

# Exporta o modelo para um formato de arquivo compatível com o Roblox
export_path = "caminho/para/o/modelo.fbx"
bpy.ops.export_scene.fbx(filepath=export_path)

# Cria uma nova instância do Roblox
roblox = roblox.Roblox()

# Faz login no Roblox
roblox.login("nome_de_usuário", "senha")

# Cria um novo jogo no Roblox
game = roblox.create_game("Nome do jogo")

# Importa o modelo para o jogo
model_id = roblox.import_model(export_path)

# Adiciona o modelo ao jogo
roblox.add_model_to_game(game.id, model_id)

# Publica o jogo
roblox.publish_game(game.id)
```



#### **Observações:**

- Você precisará substituir "caminho/para/o/modelo.fbx" pelo caminho real para o arquivo do modelo 3D.
- Você precisará substituir "Nome do jogo" pelo nome que deseja dar ao seu jogo Roblox.
- Você precisará substituir "nome_de_usuário" e "senha" pelas suas credenciais de login do Roblox.

Este script importará o modelo 3D personalizado para o Roblox Studio, criará um novo material para o modelo, exportará o modelo para um formato de arquivo compatível com o Roblox, criará um novo jogo no Roblox, importará o modelo para o jogo e publicará o jogo.





## **Metodo de construção**



#### **Como criar jogos Roblox:**

1. **Abra o Roblox Studio.**
2. **Clique no botão \**Criar novo\**.**
3. **Selecione um modelo para o seu jogo.**
4. **Clique no botão \**Criar\**.**
5. **Comece a criar seu jogo!**



Você pode usar as ferramentas no Roblox Studio para criar seu mundo, adicionar objetos e personagens e escrever scripts para controlar o comportamento do jogo.



#### **Aqui estão algumas dicas para criar jogos Roblox:**

- **Comece pequeno.** Não tente criar um jogo muito complexo em seu primeiro projeto.
- **Use os recursos disponíveis.** O Roblox Studio possui uma ampla variedade de ferramentas e recursos para ajudá-lo a criar seu jogo.
- **Aprenda com os outros.** Existem muitos recursos online e comunidades onde você pode aprender sobre o desenvolvimento de jogos Roblox.
- **Seja criativo!** O Roblox oferece infinitas possibilidades para criar jogos únicos e divertidos.



#### **Aqui estão alguns jogos Roblox populares que você pode criar:**

- **Jogos de aventura:** Explore mundos diferentes, resolva quebra-cabeças e lute contra inimigos.
- **Jogos de construção:** Crie seus próprios mundos e estruturas.
- **Jogos de corrida:** Corra contra outros jogadores ou contra o relógio.
- **Jogos de tiro:** Atire em inimigos e complete missões.
- **Jogos de RPG:** Crie seu próprio personagem e embarque em uma jornada épica.



#### **Depois de criar seu jogo, você pode publicá-lo no Roblox para que outras pessoas possam jogá-lo.**



#### **Observações:**

- O Roblox Studio é gratuito para usar.
- Você pode encontrar muitos tutoriais e recursos online para ajudá-lo a aprender como criar jogos Roblox.
- Seja paciente e persistente. Criar jogos Roblox pode ser desafiador, mas também é muito recompensador.





### **Programas:**

- Roblox Studio
- Blender
- GIMP
- Audacity



#### **Códigos:**

- Lua (linguagem de script do Roblox)
- Python
- C++
- HTML
- CSS



#### **Apps:**

- Roblox Mobile
- Roblox Player
- Roblox Creator Companion
- Roblox Studio Mobile



#### **Como usar esses programas, códigos e apps para criar uma experiência no Roblox:**



- **Roblox Studio:** Use o Roblox Studio para criar e editar experiências do Roblox.
- **Blender:** Use o Blender para criar modelos e animações 3D para suas experiências do Roblox.
- **GIMP:** Use o GIMP para criar e editar imagens para suas experiências do Roblox.
- **Audacity:** Use o Audacity para criar e editar áudio para suas experiências do Roblox.
- **Lua:** Use a linguagem de script Lua para programar suas experiências do Roblox.
- **Python:** Use Python para criar scripts e plugins para suas experiências do Roblox.
- **C++:** Use C++ para criar plugins de alto desempenho para suas experiências do Roblox.
- **HTML:** Use HTML para criar interfaces de usuário personalizadas para suas experiências do Roblox.
- **CSS:** Use CSS para estilizar as interfaces de usuário personalizadas de suas experiências do Roblox.
- **Roblox Mobile:** Use o Roblox Mobile para jogar experiências do Roblox em seu dispositivo móvel.
- **Roblox Player:** Use o Roblox Player para jogar experiências do Roblox em seu computador.
- **Roblox Creator Companion:** Use o Roblox Creator Companion para criar e gerenciar suas experiências do Roblox em seu dispositivo móvel.
- **Roblox Studio Mobile:** Use o Roblox Studio Mobile para criar e editar experiências do Roblox em seu dispositivo móvel.



#### **Observações:**

- Você não precisa usar todos esses programas, códigos e apps para criar uma experiência no Roblox.
- Você pode usar os programas, códigos e apps que melhor se adequam às suas necessidades e habilidades.
- Há muitos recursos disponíveis online para ajudá-lo a aprender como usar esses programas, códigos e apps.





### **Vide site:**

Hands-on: Criando um Jogo de Sobrevivência no Roblox   https://www.roblox.com/games/11540492058/Survival-Game-SSC

https://tecnobits.com/pt/como-colocar-roblox-em-tela-cheia-no-pc/

https://clubedovideogame.com.br/melhores-jogos-do-roblox/

https://create.roblox.com/

--========================================================--
-- SISTEMA DE PLACAS / EXÉRCITO ROBLOX
-- LocalScript em StarterPlayerScripts
--========================================================--

local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")
local TextChatService = game:GetService("TextChatService")

local player = Players.LocalPlayer

--========================================================--
-- GUI PRINCIPAL
--========================================================--

local gui = Instance.new("ScreenGui")
gui.Name = "MenuExercito"
gui.ResetOnSpawn = false
gui.IgnoreGuiInset = true
gui.Parent = player:WaitForChild("PlayerGui")

--========================================================--
-- TELA DE INICIALIZAÇÃO
--========================================================--

local intro = Instance.new("Frame")
intro.Size = UDim2.new(1, 0, 1, 0)
intro.BackgroundColor3 = Color3.fromRGB(3, 3, 8)
intro.BorderSizePixel = 0
intro.ZIndex = 100
intro.Parent = gui

local fundoGradiente = Instance.new("UIGradient")
fundoGradiente.Color = ColorSequence.new({
	ColorSequenceKeypoint.new(0, Color3.fromRGB(2, 5, 15)),
	ColorSequenceKeypoint.new(0.5, Color3.fromRGB(5, 5, 12)),
	ColorSequenceKeypoint.new(1, Color3.fromRGB(2, 2, 5))
})
fundoGradiente.Rotation = 90
fundoGradiente.Parent = intro

-- Linha superior
local linhaSuperior = Instance.new("Frame")
linhaSuperior.Size = UDim2.new(0, 0, 0, 3)
linhaSuperior.Position = UDim2.new(0.5, 0, 0.25, 0)
linhaSuperior.AnchorPoint = Vector2.new(0.5, 0.5)
linhaSuperior.BackgroundColor3 = Color3.fromRGB(0, 200, 255)
linhaSuperior.BorderSizePixel = 0
linhaSuperior.ZIndex = 101
linhaSuperior.Parent = intro

local glowSuperior = Instance.new("UIStroke")
glowSuperior.Color = Color3.fromRGB(0, 200, 255)
glowSuperior.Thickness = 2
glowSuperior.Parent = linhaSuperior

-- Título
local tituloIntro = Instance.new("TextLabel")
tituloIntro.Size = UDim2.new(0.9, 0, 0, 60)
tituloIntro.Position = UDim2.new(0.5, 0, 0.38, 0)
tituloIntro.AnchorPoint = Vector2.new(0.5, 0.5)
tituloIntro.BackgroundTransparency = 1
tituloIntro.Text = "🎖️ EXÉRCITO ROBLOX"
tituloIntro.TextColor3 = Color3.fromRGB(255, 255, 255)
tituloIntro.TextSize = 32
tituloIntro.Font = Enum.Font.GothamBold
tituloIntro.TextTransparency = 1
tituloIntro.ZIndex = 101
tituloIntro.Parent = intro

local tituloStroke = Instance.new("UIStroke")
tituloStroke.Color = Color3.fromRGB(0, 200, 255)
tituloStroke.Thickness = 1.5
tituloStroke.Parent = tituloIntro

-- Criador
local criadorIntro = Instance.new("TextLabel")
criadorIntro.Size = UDim2.new(0.9, 0, 0, 45)
criadorIntro.Position = UDim2.new(0.5, 0, 0.48, 0)
criadorIntro.AnchorPoint = Vector2.new(0.5, 0.5)
criadorIntro.BackgroundTransparency = 1
criadorIntro.Text = "Script feito por General de Divisão Ghost."
criadorIntro.TextColor3 = Color3.fromRGB(0, 220, 255)
criadorIntro.TextSize = 20
criadorIntro.Font = Enum.Font.GothamMedium
criadorIntro.TextTransparency = 1
criadorIntro.ZIndex = 101
criadorIntro.Parent = intro

local criadorStroke = Instance.new("UIStroke")
criadorStroke.Color = Color3.fromRGB(0, 150, 255)
criadorStroke.Thickness = 1
criadorStroke.Parent = criadorIntro

-- Linha inferior
local linhaInferior = Instance.new("Frame")
linhaInferior.Size = UDim2.new(0, 0, 0, 3)
linhaInferior.Position = UDim2.new(0.5, 0, 0.65, 0)
linhaInferior.AnchorPoint = Vector2.new(0.5, 0.5)
linhaInferior.BackgroundColor3 = Color3.fromRGB(0, 200, 255)
linhaInferior.BorderSizePixel = 0
linhaInferior.ZIndex = 101
linhaInferior.Parent = intro

local glowInferior = Instance.new("UIStroke")
glowInferior.Color = Color3.fromRGB(0, 200, 255)
glowInferior.Thickness = 2
glowInferior.Parent = linhaInferior

-- Detalhes neon
local detalhes = {}

for i = 1, 10 do
	local detalhe = Instance.new("Frame")

	detalhe.Size = UDim2.new(0, 5, 0, 5)
	detalhe.Position = UDim2.new(
		math.random(5, 95) / 100,
		0,
		math.random(10, 90) / 100,
		0
	)

	detalhe.BackgroundColor3 = Color3.fromRGB(0, 200, 255)
	detalhe.BorderSizePixel = 0
	detalhe.ZIndex = 101
	detalhe.Parent = intro

	local c = Instance.new("UICorner")
	c.CornerRadius = UDim.new(1, 0)
	c.Parent = detalhe

	table.insert(detalhes, detalhe)
end

-- Animação da intro
TweenService:Create(
	linhaSuperior,
	TweenInfo.new(0.8, Enum.EasingStyle.Quart, Enum.EasingDirection.Out),
	{Size = UDim2.new(0.45, 0, 0, 3)}
):Play()

TweenService:Create(
	linhaInferior,
	TweenInfo.new(0.8, Enum.EasingStyle.Quart, Enum.EasingDirection.Out),
	{Size = UDim2.new(0.30, 0, 0, 3)}
):Play()

task.wait(0.3)

TweenService:Create(
	tituloIntro,
	TweenInfo.new(0.8, Enum.EasingStyle.Quart, Enum.EasingDirection.Out),
	{TextTransparency = 0}
):Play()

task.wait(0.3)

TweenService:Create(
	criadorIntro,
	TweenInfo.new(0.8, Enum.EasingStyle.Quart, Enum.EasingDirection.Out),
	{TextTransparency = 0}
):Play()

task.spawn(function()
	while intro.Parent do

		for _, detalhe in ipairs(detalhes) do
			TweenService:Create(
				detalhe,
				TweenInfo.new(0.6),
				{BackgroundTransparency = 0.7}
			):Play()
		end

		task.wait(0.6)

		for _, detalhe in ipairs(detalhes) do
			TweenService:Create(
				detalhe,
				TweenInfo.new(0.6),
				{BackgroundTransparency = 0}
			):Play()
		end

		task.wait(0.6)
	end
end)

task.wait(2.5)

local introOut = TweenInfo.new(
	0.8,
	Enum.EasingStyle.Quart,
	Enum.EasingDirection.In
)

TweenService:Create(
	tituloIntro,
	introOut,
	{TextTransparency = 1}
):Play()

TweenService:Create(
	criadorIntro,
	introOut,
	{TextTransparency = 1}
):Play()

local fade = TweenService:Create(
	intro,
	introOut,
	{BackgroundTransparency = 1}
)

fade:Play()
fade.Completed:Wait()

intro:Destroy()

--========================================================--
-- LOGO
--========================================================--

local toggle = Instance.new("TextButton")
toggle.Size = UDim2.new(0, 130, 0, 40)
toggle.Position = UDim2.new(0, 20, 0.5, -20)
toggle.Text = "📋 PLACAS"
toggle.TextSize = 18
toggle.Font = Enum.Font.GothamBold
toggle.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
toggle.TextColor3 = Color3.new(1, 1, 1)
toggle.BorderSizePixel = 0
toggle.Active = true
toggle.Parent = gui

local toggleCorner = Instance.new("UICorner")
toggleCorner.CornerRadius = UDim.new(0, 8)
toggleCorner.Parent = toggle

--========================================================--
-- MENU
--========================================================--

local menu = Instance.new("Frame")
menu.Size = UDim2.new(0, 300, 0, 390)
menu.Position = UDim2.new(0, -320, 0.5, 30)
menu.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
menu.BorderSizePixel = 0
menu.Visible = false
menu.Active = true
menu.Parent = gui

local menuCorner = Instance.new("UICorner")
menuCorner.CornerRadius = UDim.new(0, 10)
menuCorner.Parent = menu

--========================================================--
-- TÍTULO
--========================================================--

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, -55, 0, 45)
title.Position = UDim2.new(0, 10, 0, 0)
title.Text = "🎖️ EXÉRCITO ROBLOX"
title.TextSize = 20
title.Font = Enum.Font.GothamBold
title.TextColor3 = Color3.new(1, 1, 1)
title.BackgroundTransparency = 1
title.TextXAlignment = Enum.TextXAlignment.Left
title.Active = true
title.Parent = menu

--========================================================--
-- X
--========================================================--

local closeButton = Instance.new("TextButton")
closeButton.Size = UDim2.new(0, 38, 0, 38)
closeButton.Position = UDim2.new(1, -43, 0, 4)
closeButton.Text = "✕"
closeButton.TextSize = 24
closeButton.Font = Enum.Font.GothamBold
closeButton.TextColor3 = Color3.new(1, 1, 1)
closeButton.BackgroundColor3 = Color3.fromRGB(180, 45, 45)
closeButton.BorderSizePixel = 0
closeButton.Parent = menu

local closeCorner = Instance.new("UICorner")
closeCorner.CornerRadius = UDim.new(0, 8)
closeCorner.Parent = closeButton

--========================================================--
-- ÁREA DE ROLAGEM
--========================================================--

local scroll = Instance.new("ScrollingFrame")
scroll.Size = UDim2.new(1, -20, 1, -55)
scroll.Position = UDim2.new(0, 10, 0, 50)
scroll.BackgroundTransparency = 1
scroll.BorderSizePixel = 0
scroll.ScrollBarThickness = 6
scroll.ScrollBarImageColor3 = Color3.fromRGB(0, 180, 255)
scroll.CanvasSize = UDim2.new(0, 0, 0, 0)
scroll.ScrollingDirection = Enum.ScrollingDirection.Y
scroll.Active = true
scroll.Parent = menu

local layout = Instance.new("UIListLayout")
layout.Padding = UDim.new(0, 8)
layout.HorizontalAlignment = Enum.HorizontalAlignment.Center
layout.Parent = scroll

--========================================================--
-- FUNÇÃO PARA CRIAR BOTÃO
--========================================================--

local function criarBotao(nome, tamanho)

	local button = Instance.new("TextButton")

	button.Size = UDim2.new(1, -5, 0, tamanho or 45)
	button.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
	button.TextColor3 = Color3.new(1, 1, 1)
	button.TextSize = 16
	button.Font = Enum.Font.GothamBold
	button.Text = nome
	button.TextWrapped = true
	button.BorderSizePixel = 0
	button.AutoButtonColor = true
	button.Parent = scroll

	local corner = Instance.new("UICorner")
	corner.CornerRadius = UDim.new(0, 7)
	corner.Parent = button

	return button
end

--========================================================--
-- PATENTES
--========================================================--

local patentes = {
	"Recruta",
	"Soldado",
	"Cabo",
	"3º Sargento",
	"2º Sargento",
	"1º Sargento",
	"Subtenente",
	"Aspirante a Oficial",
	"2º Tenente",
	"1º Tenente",
	"Capitão"
}

local textoPatentes = table.concat(patentes, "\n")

--========================================================--
-- PLACAS / COMANDOS
--========================================================--

local placas = {

	{
		nome = "🎖️ FILA ÚNICA",
		texto = "🎖️ FILA ÚNICA\n\nFormem uma fila com apenas uma pessoa por linha.\n\nMantenham distância e aguardem as instruções."
	},

	{
		nome = "🎖️ STS",
		texto = "🎖️ STS\n\nShoulder To Shoulder.\n\nFiquem lado a lado, ombro a ombro, sem deixar espaços."
	},

	{
		nome = "🎖️ FORMAÇÃO",
		texto = "🎖️ FORMAÇÃO\n\nMantenham-se alinhados e em silêncio.\n\nAguardem o próximo comando."
	},

	{
		nome = "🎖️ SENTIDO!",
		texto = "🎖️ SENTIDO!\n\nFiquem parados, olhando para o superior.\n\nNão se movimentem até receber outro comando."
	},

	{
		nome = "🎖️ DESCANSAR!",
		texto = "🎖️ DESCANSAR!\n\nPodem relaxar a postura, mas permaneçam no local e aguardem o próximo comando."
	},

	{
		nome = "🎖️ À VONTADE!",
		texto = "🎖️ À VONTADE!\n\nPodem se movimentar livremente no local.\n\nAguardem novas instruções."
	}
}

--========================================================--
-- CHAT
--========================================================--

local function enviarMensagem(texto)

	local canais = TextChatService:FindFirstChild("TextChannels")

	if not canais then
		return
	end

	local general = canais:FindFirstChild("RBXGeneral")

	if general then
		general:SendAsync(texto)
	end
end

--========================================================--
-- TÍTULO DA SEÇÃO
--========================================================--

local function criarTituloSecao(texto)

	local label = Instance.new("TextLabel")

	label.Size = UDim2.new(1, -5, 0, 35)
	label.BackgroundTransparency = 1
	label.Text = texto
	label.TextColor3 = Color3.fromRGB(0, 200, 255)
	label.TextSize = 18
	label.Font = Enum.Font.GothamBold
	label.Parent = scroll

	return label
end

--========================================================--
-- SEÇÃO: PLACAS
--========================================================--

criarTituloSecao("━━━ 🎖️ COMANDOS ━━━")

for _, placaInfo in ipairs(placas) do

	local button = criarBotao(placaInfo.nome, 45)

	button.MouseButton1Click:Connect(function()
		enviarMensagem(placaInfo.texto)
	end)

end

--========================================================--
-- SEÇÃO: PATENTES
--========================================================--

criarTituloSecao("━━━ 🪖 PATENTES ━━━")

local patentesButton = criarBotao(
	"📋 VER PATENTES",
	45
)

patentesButton.MouseButton1Click:Connect(function()

	enviarMensagem("PATENTES:\n\n" .. textoPatentes)

end)

--========================================================--
-- BOTÃO COPIAR PATENTES
--========================================================--

local copiarButton = criarBotao(
	"📋 COPIAR PATENTES",
	45
)

copiarButton.MouseButton1Click:Connect(function()

	-- Roblox não disponibiliza clipboard diretamente
	-- para LocalScripts comuns.
	-- Abrimos uma caixa de texto selecionável.

	local janela = Instance.new("Frame")
	janela.Size = UDim2.new(0, 270, 0, 230)
	janela.Position = UDim2.new(0.5, -135, 0.5, -115)
	janela.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
	janela.BorderSizePixel = 0
	janela.ZIndex = 50
	janela.Parent = gui

	local c = Instance.new("UICorner")
	c.CornerRadius = UDim.new(0, 10)
	c.Parent = janela

	local titulo = Instance.new("TextLabel")
	titulo.Size = UDim2.new(1, -20, 0, 40)
	titulo.Position = UDim2.new(0, 10, 0, 5)
	titulo.BackgroundTransparency = 1
	titulo.Text = "📋 COPIAR PATENTES"
	titulo.TextColor3 = Color3.fromRGB(0, 200, 255)
	titulo.TextSize = 18
	titulo.Font = Enum.Font.GothamBold
	titulo.ZIndex = 51
	titulo.Parent = janela

	local caixa = Instance.new("TextBox")
	caixa.Size = UDim2.new(1, -20, 0, 125)
	caixa.Position = UDim2.new(0, 10, 0, 50)
	caixa.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
	caixa.TextColor3 = Color3.new(1, 1, 1)
	caixa.TextSize = 15
	caixa.Font = Enum.Font.Gotham
	caixa.Text = textoPatentes
	caixa.TextWrapped = true
	caixa.MultiLine = true
	caixa.ClearTextOnFocus = false
	caixa.ZIndex = 51
	caixa.Parent = janela

	local fechar = Instance.new("TextButton")
	fechar.Size = UDim2.new(1, -20, 0, 35)
	fechar.Position = UDim2.new(0, 10, 1, -45)
	fechar.Text = "FECHAR"
	fechar.TextSize = 15
	fechar.Font = Enum.Font.GothamBold
	fechar.TextColor3 = Color3.new(1, 1, 1)
	fechar.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
	fechar.ZIndex = 51
	fechar.Parent = janela

	local fc = Instance.new("UICorner")
	fc.CornerRadius = UDim.new(0, 6)
	fc.Parent = fechar

	fechar.MouseButton1Click:Connect(function()
		janela:Destroy()
	end)

	-- Seleciona automaticamente o texto
	task.wait()
	caixa:CaptureFocus()
	caixa.SelectionStart = 1
	caixa.CursorPosition = #caixa.Text + 1

end)

--========================================================--
-- REGRAS
--========================================================--

criarTituloSecao("━━━ 📖 REGRAS ━━━")

local regras = {

	{
		nome = "📜 REGRA 01",
		texto = "RESPEITO\n\nRespeite todos os membros, superiores e inferiores. Evite provocações, ofensas e discussões desnecessárias."
	},

	{
		nome = "📜 REGRA 02",
		texto = "DISCIPLINA\n\nObedeça aos comandos dos superiores responsáveis durante treinamentos e atividades."
	},

	{
		nome = "📜 REGRA 03",
		texto = "UNIFORME\n\nUtilize o uniforme e os acessórios determinados pelo grupo durante as atividades oficiais."
	},

	{
		nome = "📜 REGRA 04",
		texto = "FORMAÇÃO\n\nDurante formações, mantenha seu lugar, fique atento aos comandos e evite movimentações desnecessárias."
	},

	{
		nome = "📜 REGRA 05",
		texto = "CHAT\n\nUtilize o chat de maneira adequada. Evite spam, flood e mensagens que atrapalhem os treinamentos."
	},

	{
		nome = "📜 REGRA 06",
		texto = "HIERARQUIA\n\nRespeite a hierarquia do grupo e procure os responsáveis quando precisar de ajuda ou tiver alguma dúvida."
	}
}

for _, regra in ipairs(regras) do

	local button = criarBotao(regra.nome, 45)

	button.MouseButton1Click:Connect(function()

		enviarMensagem(
			"📖 " .. regra.texto
		)

	end)

end

--========================================================--
-- COMANDOS DE MARCHA
--========================================================--

criarTituloSecao("━━━ 🥾 MARCHA ━━━")

local marchas = {

	{
		nome = "🥾 INICIAR MARCHA",
		texto = "🥾 INICIAR MARCHA!\n\nTodos devem seguir a formação e acompanhar o responsável."
	},

	{
		nome = "🛑 PARAR MARCHA",
		texto = "🛑 PARAR MARCHA!\n\nInterrompam o deslocamento e aguardem novas instruções."
	},

	{
		nome = "↩️ RETORNAR",
		texto = "↩️ RETORNAR!\n\nRetornem ao local determinado mantendo a formação."
	}
}

for _, marcha in ipairs(marchas) do

	local button = criarBotao(marcha.nome, 45)

	button.MouseButton1Click:Connect(function()
		enviarMensagem(marcha.texto)
	end)

end

--========================================================--
-- INFORMAÇÕES
--========================================================--

criarTituloSecao("━━━ ℹ️ INFORMAÇÕES ━━━")

local infoButton = criarBotao(
	"ℹ️ INFORMAÇÕES DO SISTEMA",
	45
)

infoButton.MouseButton1Click:Connect(function()

	enviarMensagem(
		"🎖️ SISTEMA DE PLACAS\n\n" ..
		"Utilize os comandos disponíveis no menu para auxiliar nas atividades do Exército Roblox."
	)

end)

--========================================================--
-- TWEEN DO MENU
--========================================================--

local menuAberto = false
local animando = false

local menuAbertoPos = UDim2.new(0, 20, 0.5, 30)
local menuFechadoPos = UDim2.new(0, -320, 0.5, 30)

local tweenMenu = TweenInfo.new(
	0.45,
	Enum.EasingStyle.Quart,
	Enum.EasingDirection.Out
)

local tweenLogo = TweenInfo.new(
	0.25,
	Enum.EasingStyle.Back,
	Enum.EasingDirection.Out
)

local function abrirMenu()

	if animando then
		return
	end

	animando = true
	menuAberto = true
	menu.Visible = true

	local abrir = TweenService:Create(
		menu,
		tweenMenu,
		{Position = menuAbertoPos}
	)

	local logo = TweenService:Create(
		toggle,
		tweenLogo,
		{Size = UDim2.new(0, 140, 0, 44)}
	)

	abrir:Play()
	logo:Play()

	abrir.Completed:Wait()

	animando = false
end

local function fecharMenu()

	if animando then
		return
	end

	animando = true
	menuAberto = false

	local fechar = TweenService:Create(
		menu,
		tweenMenu,
		{Position = menuFechadoPos}
	)

	local logo = TweenService:Create(
		toggle,
		tweenLogo,
		{Size = UDim2.new(0, 130, 0, 40)}
	)

	fechar:Play()
	logo:Play()

	fechar.Completed:Wait()

	menu.Visible = false
	animando = false
end

--========================================================--
-- LOGO: ABRIR / FECHAR
--========================================================--

local ignorarClique = false

toggle.MouseButton1Click:Connect(function()

	if ignorarClique then
		ignorarClique = false
		return
	end

	if menuAberto then
		fecharMenu()
	else
		abrirMenu()
	end

end)

--========================================================--
-- X
--========================================================--

closeButton.MouseButton1Click:Connect(function()
	fecharMenu()
end)

--========================================================--
-- LOGO ARRASTÁVEL
--========================================================--

local logoDragging = false
local logoDragStart
local logoStartPosition

toggle.InputBegan:Connect(function(input)

	if input.UserInputType == Enum.UserInputType.MouseButton1
		or input.UserInputType == Enum.UserInputType.Touch then

		logoDragging = true
		logoDragStart = input.Position
		logoStartPosition = toggle.Position

		input.Changed:Connect(function()

			if input.UserInputState == Enum.UserInputState.End then
				logoDragging = false
			end

		end)
	end
end)

UserInputService.InputChanged:Connect(function(input)

	if not logoDragging then
		return
	end

	if input.UserInputType == Enum.UserInputType.MouseMovement
		or input.UserInputType == Enum.UserInputType.Touch then

		local delta = input.Position - logoDragStart

		if math.abs(delta.X) > 5 or math.abs(delta.Y) > 5 then
			ignorarClique = true
		end

		toggle.Position = UDim2.new(
			logoStartPosition.X.Scale,
			logoStartPosition.X.Offset + delta.X,
			logoStartPosition.Y.Scale,
			logoStartPosition.Y.Offset + delta.Y
		)
	end
end)

--========================================================--
-- MENU ARRASTÁVEL
--========================================================--

local menuDragging = false
local menuDragStart
local menuStartPosition

title.InputBegan:Connect(function(input)

	if input.UserInputType == Enum.UserInputType.MouseButton1
		or input.UserInputType == Enum.UserInputType.Touch then

		menuDragging = true
		menuDragStart = input.Position
		menuStartPosition = menu.Position

		input.Changed:Connect(function()

			if input.UserInputState == Enum.UserInputState.End then
				menuDragging = false
			end

		end)
	end
end)

UserInputService.InputChanged:Connect(function(input)

	if not menuDragging then
		return
	end

	if input.UserInputType == Enum.UserInputType.MouseMovement
		or input.UserInputType == Enum.UserInputType.Touch then

		local delta = input.Position - menuDragStart

		menu.Position = UDim2.new(
			menuStartPosition.X.Scale,
			menuStartPosition.X.Offset + delta.X,
			menuStartPosition.Y.Scale,
			menuStartPosition.Y.Offset + delta.Y
		)

	end

end)

--========================================================--
-- ATUALIZAR ROLAGEM DO MENU
--========================================================--

local function atualizarScroll()

	scroll.CanvasSize = UDim2.new(
		0,
		0,
		0,
		layout.AbsoluteContentSize.Y + 15
	)

end

layout:GetPropertyChangedSignal("AbsoluteContentSize"):Connect(
	atualizarScroll
)

-- Atualiza assim que o script carregar
task.defer(atualizarScroll)

--========================================================--
-- FIM DO SISTEMA
--========================================================--

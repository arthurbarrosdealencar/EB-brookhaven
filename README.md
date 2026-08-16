--========================================================--
-- 🎖️ SISTEMA DE PLACAS - EXÉRCITO ROBLOX
-- LocalScript em StarterPlayerScripts
--========================================================--

local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")
local TextChatService = game:GetService("TextChatService")

local player = Players.LocalPlayer

--========================================================--
-- ⚙️ CONFIGURAÇÕES
--========================================================--

local IMAGE_ID = "rbxassetid://COLOQUE_SEU_ID_AQUI"

local NEON = Color3.fromRGB(0, 200, 255)

--========================================================--
-- GUI
--========================================================--

local gui = Instance.new("ScreenGui")
gui.Name = "MenuExercito"
gui.ResetOnSpawn = false
gui.IgnoreGuiInset = true
gui.Parent = player:WaitForChild("PlayerGui")

--========================================================--
-- 🌑 TELA DE INICIALIZAÇÃO
--========================================================--

local intro = Instance.new("Frame")
intro.Size = UDim2.new(1,0,1,0)
intro.BackgroundColor3 = Color3.fromRGB(2,3,8)
intro.BorderSizePixel = 0
intro.ZIndex = 100
intro.Parent = gui

local introTitle = Instance.new("TextLabel")
introTitle.Size = UDim2.new(0.9,0,0,70)
introTitle.Position = UDim2.new(0.5,0,0.4,0)
introTitle.AnchorPoint = Vector2.new(0.5,0.5)
introTitle.BackgroundTransparency = 1
introTitle.Text = "🎖️ EXÉRCITO ROBLOX"
introTitle.TextColor3 = Color3.new(1,1,1)
introTitle.TextSize = 30
introTitle.Font = Enum.Font.GothamBold
introTitle.TextTransparency = 1
introTitle.ZIndex = 101
introTitle.Parent = intro

local introStroke = Instance.new("UIStroke")
introStroke.Color = NEON
introStroke.Thickness = 2
introStroke.Parent = introTitle

local introCreator = Instance.new("TextLabel")
introCreator.Size = UDim2.new(0.9,0,0,50)
introCreator.Position = UDim2.new(0.5,0,0.5,0)
introCreator.AnchorPoint = Vector2.new(0.5,0.5)
introCreator.BackgroundTransparency = 1
introCreator.Text = "Script feito por General de Divisão Ghost."
introCreator.TextColor3 = NEON
introCreator.TextSize = 19
introCreator.Font = Enum.Font.Gotham
introCreator.TextTransparency = 1
introCreator.ZIndex = 101
introCreator.Parent = intro

local linha = Instance.new("Frame")
linha.Size = UDim2.new(0,0,0,3)
linha.Position = UDim2.new(0.5,0,0.58,0)
linha.AnchorPoint = Vector2.new(0.5,0.5)
linha.BackgroundColor3 = NEON
linha.BorderSizePixel = 0
linha.ZIndex = 101
linha.Parent = intro

TweenService:Create(
	linha,
	TweenInfo.new(0.8,Enum.EasingStyle.Quart,Enum.EasingDirection.Out),
	{Size = UDim2.new(0.45,0,0,3)}
):Play()

task.wait(0.4)

TweenService:Create(
	introTitle,
	TweenInfo.new(0.7),
	{TextTransparency = 0}
):Play()

task.wait(0.3)

TweenService:Create(
	introCreator,
	TweenInfo.new(0.7),
	{TextTransparency = 0}
):Play()

task.wait(2)

TweenService:Create(
	introTitle,
	TweenInfo.new(0.5),
	{TextTransparency = 1}
):Play()

TweenService:Create(
	introCreator,
	TweenInfo.new(0.5),
	{TextTransparency = 1}
):Play()

TweenService:Create(
	intro,
	TweenInfo.new(0.7),
	{BackgroundTransparency = 1}
):Play()

task.wait(0.8)
intro:Destroy()

--========================================================--
-- 🖼️ LOGO
--========================================================--

local toggle = Instance.new("ImageButton")
toggle.Name = "LogoPlacas"
toggle.Size = UDim2.new(0,72,0,72)
toggle.Position = UDim2.new(0,20,0.5,-36)
toggle.BackgroundColor3 = Color3.fromRGB(5,8,15)
toggle.BorderSizePixel = 0
toggle.Image = IMAGE_ID
toggle.ScaleType = Enum.ScaleType.Crop
toggle.AutoButtonColor = false
toggle.Active = true
toggle.Parent = gui

local logoCorner = Instance.new("UICorner")
logoCorner.CornerRadius = UDim.new(0,12)
logoCorner.Parent = toggle

local logoStroke = Instance.new("UIStroke")
logoStroke.Color = NEON
logoStroke.Thickness = 3
logoStroke.Parent = toggle

local logoGlow = Instance.new("UIStroke")
logoGlow.Color = Color3.fromRGB(0,80,255)
logoGlow.Thickness = 8
logoGlow.Transparency = 0.65
logoGlow.Parent = toggle

task.spawn(function()

	while toggle.Parent do

		TweenService:Create(
			logoGlow,
			TweenInfo.new(1),
			{Transparency = 0.25}
		):Play()

		task.wait(1)

		TweenService:Create(
			logoGlow,
			TweenInfo.new(1),
			{Transparency = 0.7}
		):Play()

		task.wait(1)

	end

end)

--========================================================--
-- 📋 MENU
--========================================================--

local menu = Instance.new("Frame")
menu.Name = "MenuPrincipal"
menu.Size = UDim2.new(0,310,0,400)
menu.Position = UDim2.new(0,-330,0.5,30)
menu.BackgroundColor3 = Color3.fromRGB(10,15,24)
menu.BorderSizePixel = 0
menu.Visible = false
menu.Active = true
menu.Parent = gui

local menuCorner = Instance.new("UICorner")
menuCorner.CornerRadius = UDim.new(0,12)
menuCorner.Parent = menu

local menuStroke = Instance.new("UIStroke")
menuStroke.Color = NEON
menuStroke.Thickness = 2
menuStroke.Parent = menu

local menuGlow = Instance.new("UIStroke")
menuGlow.Color = Color3.fromRGB(0,80,255)
menuGlow.Thickness = 7
menuGlow.Transparency = 0.7
menuGlow.Parent = menu

local menuGradient = Instance.new("UIGradient")
menuGradient.Color = ColorSequence.new({
	ColorSequenceKeypoint.new(0,Color3.fromRGB(10,22,35)),
	ColorSequenceKeypoint.new(0.5,Color3.fromRGB(18,20,30)),
	ColorSequenceKeypoint.new(1,Color3.fromRGB(5,10,18))
})
menuGradient.Rotation = 90
menuGradient.Parent = menu

--========================================================--
-- TÍTULO
--========================================================--

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1,-60,0,48)
title.Position = UDim2.new(0,12,0,0)
title.BackgroundTransparency = 1
title.Text = "🎖️ EXÉRCITO ROBLOX"
title.TextColor3 = Color3.new(1,1,1)
title.TextSize = 20
title.Font = Enum.Font.GothamBold
title.TextXAlignment = Enum.TextXAlignment.Left
title.Active = true
title.ZIndex = 4
title.Parent = menu

local titleStroke = Instance.new("UIStroke")
titleStroke.Color = NEON
titleStroke.Thickness = 1
titleStroke.Parent = title

--========================================================--
-- ❌ FECHAR
--========================================================--

local closeButton = Instance.new("TextButton")
closeButton.Size = UDim2.new(0,38,0,38)
closeButton.Position = UDim2.new(1,-43,0,5)
closeButton.Text = "✕"
closeButton.TextSize = 23
closeButton.Font = Enum.Font.GothamBold
closeButton.TextColor3 = Color3.new(1,1,1)
closeButton.BackgroundColor3 = Color3.fromRGB(100,25,35)
closeButton.BorderSizePixel = 0
closeButton.ZIndex = 5
closeButton.Parent = menu

local closeCorner = Instance.new("UICorner")
closeCorner.CornerRadius = UDim.new(0,8)
closeCorner.Parent = closeButton

--========================================================--
-- 📜 SCROLL
--========================================================--

local scroll = Instance.new("ScrollingFrame")
scroll.Size = UDim2.new(1,-20,1,-65)
scroll.Position = UDim2.new(0,10,0,58)
scroll.BackgroundTransparency = 1
scroll.BorderSizePixel = 0
scroll.ScrollBarThickness = 5
scroll.ScrollBarImageColor3 = NEON
scroll.Active = true
scroll.Parent = menu

local layout = Instance.new("UIListLayout")
layout.Padding = UDim.new(0,8)
layout.HorizontalAlignment = Enum.HorizontalAlignment.Center
layout.Parent = scroll

--========================================================--
-- FUNÇÃO DE TÍTULO
--========================================================--

local function criarTituloSecao(texto)

	local label = Instance.new("TextLabel")

	label.Size = UDim2.new(1,-5,0,34)
	label.BackgroundTransparency = 1
	label.Text = texto
	label.TextColor3 = NEON
	label.TextSize = 17
	label.Font = Enum.Font.GothamBold
	label.Parent = scroll

	return label

end

--========================================================--
-- BOTÕES
--========================================================--

local function criarBotao(nome,tamanho)

	local button = Instance.new("TextButton")

	button.Size = UDim2.new(1,-5,0,tamanho or 45)
	button.BackgroundColor3 = Color3.fromRGB(25,32,43)
	button.TextColor3 = Color3.new(1,1,1)
	button.TextSize = 15
	button.Font = Enum.Font.GothamBold
	button.Text = nome
	button.TextWrapped = true
	button.BorderSizePixel = 0
	button.AutoButtonColor = false
	button.Parent = scroll

	local corner = Instance.new("UICorner")
	corner.CornerRadius = UDim.new(0,8)
	corner.Parent = button

	local stroke = Instance.new("UIStroke")
	stroke.Color = NEON
	stroke.Thickness = 1
	stroke.Transparency = 0.65
	stroke.Parent = button

	button.MouseEnter:Connect(function()

		TweenService:Create(
			button,
			TweenInfo.new(0.15),
			{BackgroundColor3 = Color3.fromRGB(0,75,115)}
		):Play()

		TweenService:Create(
			stroke,
			TweenInfo.new(0.15),
			{Transparency = 0}
		):Play()

	end)

	button.MouseLeave:Connect(function()

		TweenService:Create(
			button,
			TweenInfo.new(0.15),
			{BackgroundColor3 = Color3.fromRGB(25,32,43)}
		):Play()

		TweenService:Create(
			stroke,
			TweenInfo.new(0.15),
			{Transparency = 0.65}
		):Play()

	end)

	return button

end

--========================================================--
-- 💬 ENVIO DE MENSAGENS - CORRIGIDO
--========================================================--

local function enviarMensagem(texto)

	if typeof(texto) ~= "string" then
		warn("[PLACAS] Texto inválido.")
		return false
	end

	texto = texto:match("^%s*(.-)%s*$")

	if texto == "" then
		warn("[PLACAS] Mensagem vazia.")
		return false
	end

	local canais = TextChatService:WaitForChild(
		"TextChannels",
		10
	)

	if not canais then
		warn("[PLACAS] TextChannels não encontrado.")
		return false
	end

	local general = canais:WaitForChild(
		"RBXGeneral",
		10
	)

	if not general then
		warn("[PLACAS] RBXGeneral não encontrado.")
		return false
	end

	local textSource = general:FindFirstChild(
		tostring(player.UserId)
	)

	if not textSource then

		local inicio = os.clock()

		while not textSource
			and os.clock() - inicio < 5 do

			task.wait(0.1)

			textSource = general:FindFirstChild(
				tostring(player.UserId)
			)

		end

	end

	if textSource and textSource.CanSend == false then

		warn(
			"[PLACAS] Você não possui permissão para enviar mensagens."
		)

		return false

	end

	local sucesso, resultado = pcall(function()

		return general:SendAsync(texto)

	end)

	if not sucesso then

		warn(
			"[PLACAS] ERRO AO ENVIAR:",
			resultado
		)

		return false

	end

	print("[PLACAS] Mensagem enviada:",texto)

	return true

end

--========================================================--
-- 🎖️ COMANDOS
--========================================================--

local placas = {

	{
		nome = "🎖️ FILA ÚNICA",
		texto = "🎖️ FILA ÚNICA! Formem uma fila com apenas uma pessoa por linha."
	},

	{
		nome = "🎖️ STS",
		texto = "🎖️ STS! Fiquem lado a lado, ombro a ombro, sem deixar espaços."
	},

	{
		nome = "🎖️ FORMAÇÃO",
		texto = "🎖️ FORMAÇÃO! Mantenham-se alinhados e em silêncio."
	},

	{
		nome = "🎖️ SENTIDO!",
		texto = "🎖️ SENTIDO! Fiquem parados, olhando para o superior."
	},

	{
		nome = "🎖️ DESCANSAR!",
		texto = "🎖️ DESCANSAR! Relaxem a postura e aguardem o próximo comando."
	},

	{
		nome = "🎖️ À VONTADE!",
		texto = "🎖️ À VONTADE! Podem se movimentar livremente no local."
	}

}

criarTituloSecao("━━━ 🎖️ COMANDOS ━━━")

for _,placa in ipairs(placas) do

	local button = criarBotao(
		placa.nome,
		48
	)

	button.MouseButton1Click:Connect(function()

		enviarMensagem(placa.texto)

	end)

end

--========================================================--
-- 🪖 PATENTES
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

criarTituloSecao("━━━ 🪖 PATENTES ━━━")

local patenteButton = criarBotao(
	"🪖 VER PATENTES",
	48
)

patenteButton.MouseButton1Click:Connect(function()

	enviarMensagem(
		"🪖 PATENTES: " ..
		table.concat(patentes," → ")
	)

end)

--========================================================--
-- 📋 COPIAR PATENTES
--========================================================--

local copiar = criarBotao(
	"📋 COPIAR PATENTES",
	48
)

copiar.MouseButton1Click:Connect(function()

	local texto = table.concat(patentes,"\n")

	if setclipboard then
		setclipboard(texto)
		print("[PLACAS] Patentes copiadas.")
	else
		warn("[PLACAS] Clipboard não disponível.")
	end

end)

--========================================================--
-- 📖 REGRAS
--========================================================--

local regras = {

	"📜 REGRA 01 — Respeite todos os membros, superiores e inferiores.",

	"📜 REGRA 02 — Obedeça aos comandos dos superiores responsáveis.",

	"📜 REGRA 03 — Utilize o uniforme determinado pelo grupo.",

	"📜 REGRA 04 — Durante formações, mantenha seu lugar.",

	"📜 REGRA 05 — Evite spam e flood durante as atividades.",

	"📜 REGRA 06 — Respeite a hierarquia do grupo."

}

criarTituloSecao("━━━ 📖 REGRAS ━━━")

for _,regra in ipairs(regras) do

	local button = criarBotao(
		regra,
		55
	)

	button.MouseButton1Click:Connect(function()

		enviarMensagem(regra)

	end)

end

--========================================================--
-- 🥾 MARCHA
--========================================================--

criarTituloSecao("━━━ 🥾 MARCHA ━━━")

local marchas = {

	{
		nome = "🥾 INICIAR MARCHA",
		texto = "🥾 INICIAR MARCHA! Todos devem seguir a formação."
	},

	{
		nome = "🛑 PARAR MARCHA",
		texto = "🛑 PARAR MARCHA! Interrompam o deslocamento."
	},

	{
		nome = "↩️ RETORNAR",
		texto = "↩️ RETORNAR! Retornem ao local determinado."
	}

}

for _,marcha in ipairs(marchas) do

	local button = criarBotao(
		marcha.nome,
		48
	)

	button.MouseButton1Click:Connect(function()

		enviarMensagem(marcha.texto)

	end)

end

--========================================================--
-- ℹ️ INFORMAÇÕES
--========================================================--

criarTituloSecao("━━━ ℹ️ INFORMAÇÕES ━━━")

local info = criarBotao(
	"ℹ️ INFORMAÇÕES DO SISTEMA",
	48
)

info.MouseButton1Click:Connect(function()

	enviarMensagem(
		"🎖️ SISTEMA DE PLACAS — Utilize o menu para auxiliar nas atividades."
	)

end)

--========================================================--
-- 📜 SCROLL
--========================================================--

local function atualizarScroll()

	scroll.CanvasSize = UDim2.new(
		0,
		0,
		0,
		layout.AbsoluteContentSize.Y + 20
	)

end

layout:GetPropertyChangedSignal(
	"AbsoluteContentSize"
):Connect(atualizarScroll)

task.defer(atualizarScroll)

--========================================================--
-- ✨ ABRIR / FECHAR
--========================================================--

local menuAberto = false
local animando = false

local posAberto = UDim2.new(0,20,0.5,30)
local posFechado = UDim2.new(0,-330,0.5,30)

local tweenInfo = TweenInfo.new(
	0.45,
	Enum.EasingStyle.Quart,
	Enum.EasingDirection.Out
)

local function abrirMenu()

	if animando then return end

	animando = true
	menuAberto = true
	menu.Visible = true

	local tween = TweenService:Create(
		menu,
		tweenInfo,
		{Position = posAberto}
	)

	tween:Play()
	tween.Completed:Wait()

	animando = false

end

local function fecharMenu()

	if animando then return end

	animando = true
	menuAberto = false

	local tween = TweenService:Create(
		menu,
		tweenInfo,
		{Position = posFechado}
	)

	tween:Play()
	tween.Completed:Wait()

	menu.Visible = false

	animando = false

end

--========================================================--
-- 🖱️ LOGO
--========================================================--

local logoDragging = false
local logoDragStart
local logoStartPosition
local ignorarClique = false

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

	if not logoDragging then return end

	if input.UserInputType == Enum.UserInputType.MouseMovement
		or input.UserInputType == Enum.UserInputType.Touch then

		local delta = input.Position - logoDragStart

		if math.abs(delta.X) > 5
			or math.abs(delta.Y) > 5 then

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
-- ❌ X
--========================================================--

closeButton.MouseButton1Click:Connect(function()
	fecharMenu()
end)

--========================================================--
-- 🖱️ MENU ARRASTÁVEL
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

	if not menuDragging then return end

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
-- 🎖️ FIM
--========================================================--

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

-- COLOQUE AQUI O ID DA IMAGEM ENVIADA PARA O ROBLOX
local IMAGE_ID = "rbxassetid://COLOQUE_SEU_ID_AQUI"

local NEON = Color3.fromRGB(0, 200, 255)
local NEON_DARK = Color3.fromRGB(0, 80, 140)

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
intro.Name = "TelaInicial"
intro.Size = UDim2.new(1, 0, 1, 0)
intro.Position = UDim2.new(0, 0, 0, 0)
intro.BackgroundColor3 = Color3.fromRGB(2, 3, 8)
intro.BorderSizePixel = 0
intro.ZIndex = 100
intro.Parent = gui

local introGradient = Instance.new("UIGradient")
introGradient.Color = ColorSequence.new({
	ColorSequenceKeypoint.new(0, Color3.fromRGB(2, 8, 20)),
	ColorSequenceKeypoint.new(0.5, Color3.fromRGB(5, 5, 15)),
	ColorSequenceKeypoint.new(1, Color3.fromRGB(1, 2, 7))
})
introGradient.Rotation = 90
introGradient.Parent = intro

--========================================================--
-- DETALHES NEON DA INTRO
--========================================================--

local linhaSuperior = Instance.new("Frame")
linhaSuperior.Size = UDim2.new(0, 0, 0, 3)
linhaSuperior.Position = UDim2.new(0.5, 0, 0.25, 0)
linhaSuperior.AnchorPoint = Vector2.new(0.5, 0.5)
linhaSuperior.BackgroundColor3 = NEON
linhaSuperior.BorderSizePixel = 0
linhaSuperior.ZIndex = 101
linhaSuperior.Parent = intro

local linhaSuperiorGlow = Instance.new("UIStroke")
linhaSuperiorGlow.Color = NEON
linhaSuperiorGlow.Thickness = 4
linhaSuperiorGlow.Transparency = 0.4
linhaSuperiorGlow.Parent = linhaSuperior

local linhaInferior = Instance.new("Frame")
linhaInferior.Size = UDim2.new(0, 0, 0, 3)
linhaInferior.Position = UDim2.new(0.5, 0, 0.65, 0)
linhaInferior.AnchorPoint = Vector2.new(0.5, 0.5)
linhaInferior.BackgroundColor3 = NEON
linhaInferior.BorderSizePixel = 0
linhaInferior.ZIndex = 101
linhaInferior.Parent = intro

local linhaInferiorGlow = Instance.new("UIStroke")
linhaInferiorGlow.Color = NEON
linhaInferiorGlow.Thickness = 4
linhaInferiorGlow.Transparency = 0.4
linhaInferiorGlow.Parent = linhaInferior

--========================================================--
-- TÍTULO INTRO
--========================================================--

local tituloIntro = Instance.new("TextLabel")
tituloIntro.Size = UDim2.new(0.9, 0, 0, 65)
tituloIntro.Position = UDim2.new(0.5, 0, 0.39, 0)
tituloIntro.AnchorPoint = Vector2.new(0.5, 0.5)
tituloIntro.BackgroundTransparency = 1
tituloIntro.Text = "🎖️ EXÉRCITO ROBLOX"
tituloIntro.TextColor3 = Color3.new(1, 1, 1)
tituloIntro.TextSize = 32
tituloIntro.Font = Enum.Font.GothamBold
tituloIntro.TextTransparency = 1
tituloIntro.ZIndex = 101
tituloIntro.Parent = intro

local tituloStroke = Instance.new("UIStroke")
tituloStroke.Color = NEON
tituloStroke.Thickness = 2
tituloStroke.Transparency = 0.2
tituloStroke.Parent = tituloIntro

--========================================================--
-- CRIADOR
--========================================================--

local criadorIntro = Instance.new("TextLabel")
criadorIntro.Size = UDim2.new(0.9, 0, 0, 45)
criadorIntro.Position = UDim2.new(0.5, 0, 0.49, 0)
criadorIntro.AnchorPoint = Vector2.new(0.5, 0.5)
criadorIntro.BackgroundTransparency = 1
criadorIntro.Text = "Script feito por General de Divisão Ghost."
criadorIntro.TextColor3 = NEON
criadorIntro.TextSize = 20
criadorIntro.Font = Enum.Font.GothamMedium
criadorIntro.TextTransparency = 1
criadorIntro.ZIndex = 101
criadorIntro.Parent = intro

local criadorStroke = Instance.new("UIStroke")
criadorStroke.Color = NEON
criadorStroke.Thickness = 1
criadorStroke.Transparency = 0.2
criadorStroke.Parent = criadorIntro

--========================================================--
-- PARTICULAS NEON
--========================================================--

local detalhes = {}

for i = 1, 15 do

	local detalhe = Instance.new("Frame")

	detalhe.Size = UDim2.new(0, math.random(3, 6), 0, math.random(3, 6))

	detalhe.Position = UDim2.new(
		math.random(5, 95) / 100,
		0,
		math.random(10, 90) / 100,
		0
	)

	detalhe.BackgroundColor3 = NEON
	detalhe.BorderSizePixel = 0
	detalhe.ZIndex = 101
	detalhe.Parent = intro

	local c = Instance.new("UICorner")
	c.CornerRadius = UDim.new(1, 0)
	c.Parent = detalhe

	table.insert(detalhes, detalhe)
end

--========================================================--
-- ANIMAÇÃO DA INTRO
--========================================================--

TweenService:Create(
	linhaSuperior,
	TweenInfo.new(0.8, Enum.EasingStyle.Quart, Enum.EasingDirection.Out),
	{
		Size = UDim2.new(0.45, 0, 0, 3)
	}
):Play()

TweenService:Create(
	linhaInferior,
	TweenInfo.new(0.8, Enum.EasingStyle.Quart, Enum.EasingDirection.Out),
	{
		Size = UDim2.new(0.30, 0, 0, 3)
	}
):Play()

task.wait(0.3)

TweenService:Create(
	tituloIntro,
	TweenInfo.new(0.8, Enum.EasingStyle.Quart, Enum.EasingDirection.Out),
	{
		TextTransparency = 0
	}
):Play()

task.wait(0.3)

TweenService:Create(
	criadorIntro,
	TweenInfo.new(0.8, Enum.EasingStyle.Quart, Enum.EasingDirection.Out),
	{
		TextTransparency = 0
	}
):Play()

task.spawn(function()

	while intro.Parent do

		for _, detalhe in ipairs(detalhes) do

			TweenService:Create(
				detalhe,
				TweenInfo.new(0.6),
				{
					BackgroundTransparency = 0.7
				}
			):Play()

		end

		task.wait(0.6)

		for _, detalhe in ipairs(detalhes) do

			TweenService:Create(
				detalhe,
				TweenInfo.new(0.6),
				{
					BackgroundTransparency = 0
				}
			):Play()

		end

		task.wait(0.6)

	end

end)

task.wait(2.5)

TweenService:Create(
	tituloIntro,
	TweenInfo.new(0.7),
	{
		TextTransparency = 1
	}
):Play()

TweenService:Create(
	criadorIntro,
	TweenInfo.new(0.7),
	{
		TextTransparency = 1
	}
):Play()

local introFade = TweenService:Create(
	intro,
	TweenInfo.new(0.8),
	{
		BackgroundTransparency = 1
	}
)

introFade:Play()
introFade.Completed:Wait()

intro:Destroy()

--========================================================--
-- 🖼️ LOGO QUADRADA
--========================================================--

local toggle = Instance.new("ImageButton")

toggle.Name = "LogoPlacas"
toggle.Size = UDim2.new(0, 72, 0, 72)
toggle.Position = UDim2.new(0, 20, 0.5, -36)

toggle.BackgroundColor3 = Color3.fromRGB(5, 8, 15)
toggle.BorderSizePixel = 0

toggle.Image = IMAGE_ID
toggle.ScaleType = Enum.ScaleType.Crop

toggle.AutoButtonColor = false
toggle.Active = true

toggle.Parent = gui

-- Cantos arredondados
local logoCorner = Instance.new("UICorner")
logoCorner.CornerRadius = UDim.new(0, 12)
logoCorner.Parent = toggle

-- Borda neon
local logoStroke = Instance.new("UIStroke")
logoStroke.Color = NEON
logoStroke.Thickness = 3
logoStroke.Transparency = 0
logoStroke.Parent = toggle

-- Glow
local logoGlow = Instance.new("UIStroke")
logoGlow.Color = Color3.fromRGB(0, 90, 255)
logoGlow.Thickness = 8
logoGlow.Transparency = 0.65
logoGlow.Parent = toggle

--========================================================--
-- DETALHE NEON DA LOGO
--========================================================--

local logoDetalhe = Instance.new("Frame")
logoDetalhe.Size = UDim2.new(0, 18, 0, 4)
logoDetalhe.Position = UDim2.new(1, -22, 1, -8)
logoDetalhe.BackgroundColor3 = NEON
logoDetalhe.BorderSizePixel = 0
logoDetalhe.ZIndex = 5
logoDetalhe.Parent = toggle

local detalheCorner = Instance.new("UICorner")
detalheCorner.CornerRadius = UDim.new(1, 0)
detalheCorner.Parent = logoDetalhe

--========================================================--
-- ANIMAÇÃO DA LOGO
--========================================================--

task.spawn(function()

	while toggle.Parent do

		TweenService:Create(
			logoGlow,
			TweenInfo.new(
				1,
				Enum.EasingStyle.Sine,
				Enum.EasingDirection.InOut
			),
			{
				Transparency = 0.25
			}
		):Play()

		task.wait(1)

		TweenService:Create(
			logoGlow,
			TweenInfo.new(
				1,
				Enum.EasingStyle.Sine,
				Enum.EasingDirection.InOut
			),
			{
				Transparency = 0.7
			}
		):Play()

		task.wait(1)

	end

end)

--========================================================--
-- 📋 MENU
--========================================================--

local menu = Instance.new("Frame")

menu.Name = "MenuPrincipal"

menu.Size = UDim2.new(0, 310, 0, 400)

menu.Position = UDim2.new(
	0,
	-330,
	0.5,
	30
)

menu.BackgroundColor3 = Color3.fromRGB(10, 15, 24)

menu.BorderSizePixel = 0
menu.Visible = false
menu.Active = true

menu.Parent = gui

-- Cantos
local menuCorner = Instance.new("UICorner")
menuCorner.CornerRadius = UDim.new(0, 12)
menuCorner.Parent = menu

-- Borda neon
local menuStroke = Instance.new("UIStroke")
menuStroke.Color = NEON
menuStroke.Thickness = 2
menuStroke.Transparency = 0.1
menuStroke.Parent = menu

-- Glow do menu
local menuGlow = Instance.new("UIStroke")
menuGlow.Color = Color3.fromRGB(0, 80, 255)
menuGlow.Thickness = 7
menuGlow.Transparency = 0.72
menuGlow.Parent = menu

-- Gradiente
local menuGradient = Instance.new("UIGradient")

menuGradient.Color = ColorSequence.new({
	ColorSequenceKeypoint.new(
		0,
		Color3.fromRGB(10, 22, 35)
	),

	ColorSequenceKeypoint.new(
		0.5,
		Color3.fromRGB(18, 20, 30)
	),

	ColorSequenceKeypoint.new(
		1,
		Color3.fromRGB(5, 10, 18)
	)
})

menuGradient.Rotation = 90
menuGradient.Parent = menu

--========================================================--
-- TÍTULO DO MENU
--========================================================--

local title = Instance.new("TextLabel")

title.Size = UDim2.new(1, -60, 0, 48)
title.Position = UDim2.new(0, 12, 0, 0)

title.Text = "🎖️ EXÉRCITO ROBLOX"

title.TextSize = 20
title.Font = Enum.Font.GothamBold

title.TextColor3 = Color3.new(1, 1, 1)

title.BackgroundTransparency = 1

title.TextXAlignment = Enum.TextXAlignment.Left

title.Active = true

title.ZIndex = 4

title.Parent = menu

local titleStroke = Instance.new("UIStroke")
titleStroke.Color = NEON
titleStroke.Thickness = 1
titleStroke.Transparency = 0.3
titleStroke.Parent = title

--========================================================--
-- LINHA NEON DO MENU
--========================================================--

local menuLine = Instance.new("Frame")

menuLine.Size = UDim2.new(1, -20, 0, 2)
menuLine.Position = UDim2.new(0, 10, 0, 48)

menuLine.BackgroundColor3 = NEON

menuLine.BorderSizePixel = 0

menuLine.ZIndex = 4

menuLine.Parent = menu

local menuLineCorner = Instance.new("UICorner")
menuLineCorner.CornerRadius = UDim.new(1, 0)
menuLineCorner.Parent = menuLine

--========================================================--
-- ❌ BOTÃO FECHAR
--========================================================--

local closeButton = Instance.new("TextButton")

closeButton.Size = UDim2.new(0, 38, 0, 38)

closeButton.Position = UDim2.new(
	1,
	-43,
	0,
	5
)

closeButton.Text = "✕"

closeButton.TextSize = 23

closeButton.Font = Enum.Font.GothamBold

closeButton.TextColor3 = Color3.new(1, 1, 1)

closeButton.BackgroundColor3 = Color3.fromRGB(100, 25, 35)

closeButton.BorderSizePixel = 0

closeButton.ZIndex = 5

closeButton.Parent = menu

local closeCorner = Instance.new("UICorner")
closeCorner.CornerRadius = UDim.new(0, 8)
closeCorner.Parent = closeButton

local closeStroke = Instance.new("UIStroke")
closeStroke.Color = Color3.fromRGB(255, 70, 90)
closeStroke.Thickness = 1
closeStroke.Parent = closeButton

--========================================================--
-- 📜 ÁREA DE ROLAGEM
--========================================================--

local scroll = Instance.new("ScrollingFrame")

scroll.Name = "Rolagem"

scroll.Size = UDim2.new(
	1,
	-20,
	1,
	-65
)

scroll.Position = UDim2.new(
	0,
	10,
	0,
	58
)

scroll.BackgroundTransparency = 1

scroll.BorderSizePixel = 0

scroll.ScrollBarThickness = 5

scroll.ScrollBarImageColor3 = NEON

scroll.ScrollingDirection = Enum.ScrollingDirection.Y

scroll.CanvasSize = UDim2.new(0, 0, 0, 0)

scroll.Active = true

scroll.ZIndex = 2

scroll.Parent = menu

local layout = Instance.new("UIListLayout")

layout.Padding = UDim.new(0, 8)

layout.HorizontalAlignment = Enum.HorizontalAlignment.Center

layout.Parent = scroll

--========================================================--
-- FUNÇÃO CRIAR TÍTULO DE SEÇÃO
--========================================================--

local function criarTituloSecao(texto)

	local label = Instance.new("TextLabel")

	label.Size = UDim2.new(
		1,
		-5,
		0,
		34
	)

	label.BackgroundTransparency = 1

	label.Text = texto

	label.TextColor3 = NEON

	label.TextSize = 17

	label.Font = Enum.Font.GothamBold

	label.Parent = scroll

	return label
end

--========================================================--
-- FUNÇÃO CRIAR BOTÃO
--========================================================--

local function criarBotao(nome, tamanho)

	local button = Instance.new("TextButton")

	button.Size = UDim2.new(
		1,
		-5,
		0,
		tamanho or 45
	)

	button.BackgroundColor3 = Color3.fromRGB(25, 32, 43)

	button.TextColor3 = Color3.new(1, 1, 1)

	button.TextSize = 15

	button.Font = Enum.Font.GothamBold

	button.Text = nome

	button.TextWrapped = true

	button.BorderSizePixel = 0

	button.AutoButtonColor = false

	button.Parent = scroll

	local corner = Instance.new("UICorner")
	corner.CornerRadius = UDim.new(0, 8)
	corner.Parent = button

	-- Borda neon
	local stroke = Instance.new("UIStroke")

	stroke.Color = NEON

	stroke.Thickness = 1

	stroke.Transparency = 0.65

	stroke.Parent = button

	-- Hover / toque
	button.MouseEnter:Connect(function()

		TweenService:Create(
			button,
			TweenInfo.new(0.15),
			{
				BackgroundColor3 = Color3.fromRGB(
					0,
					75,
					115
				)
			}
		):Play()

		TweenService:Create(
			stroke,
			TweenInfo.new(0.15),
			{
				Transparency = 0
			}
		):Play()

	end)

	button.MouseLeave:Connect(function()

		TweenService:Create(
			button,
			TweenInfo.new(0.15),
			{
				BackgroundColor3 = Color3.fromRGB(
					25,
					32,
					43
				)
			}
		):Play()

		TweenService:Create(
			stroke,
			TweenInfo.new(0.15),
			{
				Transparency = 0.65
			}
		):Play()

	end)

	return button
end

--========================================================--
-- 💬 CHAT
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
-- 🎖️ COMANDOS
--========================================================--

local placas = {

	{
		nome = "🎖️ FILA ÚNICA",

		texto =
			"🎖️ FILA ÚNICA!\n\n" ..
			"Formem uma fila com apenas uma pessoa por linha.\n" ..
			"Mantenham distância e aguardem as instruções."
	},

	{
		nome = "🎖️ STS",

		texto =
			"🎖️ STS!\n\n" ..
			"Shoulder To Shoulder.\n" ..
			"Fiquem lado a lado, ombro a ombro, sem deixar espaços."
	},

	{
		nome = "🎖️ FORMAÇÃO",

		texto =
			"🎖️ FORMAÇÃO!\n\n" ..
			"Mantenham-se alinhados e em silêncio.\n" ..
			"Aguardem o próximo comando."
	},

	{
		nome = "🎖️ SENTIDO!",

		texto =
			"🎖️ SENTIDO!\n\n" ..
			"Fiquem parados, olhando para o superior.\n" ..
			"Não se movimentem até receber outro comando."
	},

	{
		nome = "🎖️ DESCANSAR!",

		texto =
			"🎖️ DESCANSAR!\n\n" ..
			"Relaxem a postura, permaneçam no local e aguardem o próximo comando."
	},

	{
		nome = "🎖️ À VONTADE!",

		texto =
			"🎖️ À VONTADE!\n\n" ..
			"Podem se movimentar livremente no local.\n" ..
			"Aguardem novas instruções."
	}

}

criarTituloSecao("━━━ 🎖️ COMANDOS ━━━")

for _, placa in ipairs(placas) do

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

local textoPatentes = table.concat(
	patentes,
	"\n"
)

criarTituloSecao("━━━ 🪖 PATENTES ━━━")

local verPatentes = criarBotao(
	"🪖 VER PATENTES",
	48
)

verPatentes.MouseButton1Click:Connect(function()

	enviarMensagem(
		"🪖 PATENTES:\n\n" ..
		textoPatentes
	)

end)

--========================================================--
-- 📋 COPIAR PATENTES
--========================================================--

local copiarPatentes = criarBotao(
	"📋 COPIAR PATENTES",
	48
)

copiarPatentes.MouseButton1Click:Connect(function()

	local janela = Instance.new("Frame")

	janela.Size = UDim2.new(
		0,
		280,
		0,
		250
	)

	janela.Position = UDim2.new(
		0.5,
		-140,
		0.5,
		-125
	)

	janela.BackgroundColor3 = Color3.fromRGB(8, 14, 23)

	janela.BorderSizePixel = 0

	janela.ZIndex = 50

	janela.Parent = gui

	local janelaCorner = Instance.new("UICorner")
	janelaCorner.CornerRadius = UDim.new(0, 12)
	janelaCorner.Parent = janela

	local janelaStroke = Instance.new("UIStroke")
	janelaStroke.Color = NEON
	janelaStroke.Thickness = 2
	janelaStroke.Parent = janela

	local titulo = Instance.new("TextLabel")

	titulo.Size = UDim2.new(
		1,
		-20,
		0,
		40
	)

	titulo.Position = UDim2.new(
		0,
		10,
		0,
		5
	)

	titulo.BackgroundTransparency = 1

	titulo.Text = "📋 PATENTES"

	titulo.TextColor3 = NEON

	titulo.TextSize = 18

	titulo.Font = Enum.Font.GothamBold

	titulo.ZIndex = 51

	titulo.Parent = janela

	local caixa = Instance.new("TextBox")

	caixa.Size = UDim2.new(
		1,
		-20,
		0,
		135
	)

	caixa.Position = UDim2.new(
		0,
		10,
		0,
		50
	)

	caixa.BackgroundColor3 = Color3.fromRGB(20, 27, 37)

	caixa.TextColor3 = Color3.new(1, 1, 1)

	caixa.TextSize = 15

	caixa.Font = Enum.Font.Gotham

	caixa.Text = textoPatentes

	caixa.TextWrapped = false

	caixa.MultiLine = true

	caixa.ClearTextOnFocus = false

	caixa.ZIndex = 51

	caixa.Parent = janela

	local fechar = Instance.new("TextButton")

	fechar.Size = UDim2.new(
		1,
		-20,
		0,
		38
	)

	fechar.Position = UDim2.new(
		0,
		10,
		1,
		-48
	)

	fechar.Text = "FECHAR"

	fechar.TextSize = 15

	fechar.Font = Enum.Font.GothamBold

	fechar.TextColor3 = Color3.new(1, 1, 1)

	fechar.BackgroundColor3 = Color3.fromRGB(25, 75, 105)

	fechar.BorderSizePixel = 0

	fechar.ZIndex = 51

	fechar.Parent = janela

	local fecharCorner = Instance.new("UICorner")
	fecharCorner.CornerRadius = UDim.new(0, 7)
	fecharCorner.Parent = fechar

	fechar.MouseButton1Click:Connect(function()

		janela:Destroy()

	end)

end)

--========================================================--
-- 📖 REGRAS
--========================================================--

local regras = {

	{
		nome = "📜 REGRA 01",

		texto =
			"📜 REGRA 01\n\n" ..
			"Respeite todos os membros, superiores e inferiores."
	},

	{
		nome = "📜 REGRA 02",

		texto =
			"📜 REGRA 02\n\n" ..
			"Obedeça aos comandos dos superiores responsáveis durante as atividades."
	},

	{
		nome = "📜 REGRA 03",

		texto =
			"📜 REGRA 03\n\n" ..
			"Utilize o uniforme e os acessórios determinados pelo grupo."
	},

	{
		nome = "📜 REGRA 04",

		texto =
			"📜 REGRA 04\n\n" ..
			"Durante formações, mantenha seu lugar e fique atento aos comandos."
	},

	{
		nome = "📜 REGRA 05",

		texto =
			"📜 REGRA 05\n\n" ..
			"Evite spam, flood e mensagens que atrapalhem os treinamentos."
	},

	{
		nome = "📜 REGRA 06",

		texto =
			"📜 REGRA 06\n\n" ..
			"Respeite a hierarquia e procure os responsáveis quando precisar de ajuda."
	}

}

criarTituloSecao("━━━ 📖 REGRAS ━━━")

for _, regra in ipairs(regras) do

	local button = criarBotao(
		regra.nome,
		48
	)

	button.MouseButton1Click:Connect(function()

		enviarMensagem(regra.texto)

	end)

end

--========================================================--
-- 🥾 MARCHA
--========================================================--

criarTituloSecao("━━━ 🥾 MARCHA ━━━")

local marchas = {

	{
		nome = "🥾 INICIAR MARCHA",

		texto =
			"🥾 INICIAR MARCHA!\n\n" ..
			"Todos devem seguir a formação e acompanhar o responsável."
	},

	{
		nome = "🛑 PARAR MARCHA",

		texto =
			"🛑 PARAR MARCHA!\n\n" ..
			"Interrompam o deslocamento e aguardem novas instruções."
	},

	{
		nome = "↩️ RETORNAR",

		texto =
			"↩️ RETORNAR!\n\n" ..
			"Retornem ao local determinado mantendo a formação."
	}

}

for _, marcha in ipairs(marchas) do

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

local infoButton = criarBotao(
	"ℹ️ INFORMAÇÕES DO SISTEMA",
	48
)

infoButton.MouseButton1Click:Connect(function()

	enviarMensagem(
		"🎖️ SISTEMA DE PLACAS\n\n" ..
		"Utilize o menu para auxiliar nas atividades do Exército Roblox."
	)

end)

--========================================================--
-- 📜 ATUALIZAR SCROLL
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
-- ✨ TWEENS DO MENU
--========================================================--

local menuAberto = false
local animando = false

local menuAbertoPos = UDim2.new(
	0,
	20,
	0.5,
	30
)

local menuFechadoPos = UDim2.new(
	0,
	-330,
	0.5,
	30
)

local tweenMenu = TweenInfo.new(
	0.45,
	Enum.EasingStyle.Quart,
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
		{
			Position = menuAbertoPos
		}
	)

	local logoTween = TweenService:Create(
		toggle,
		TweenInfo.new(
			0.25,
			Enum.EasingStyle.Back,
			Enum.EasingDirection.Out
		),
		{
			Size = UDim2.new(
				0,
				78,
				0,
				78
			)
		}
	)

	abrir:Play()
	logoTween:Play()

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
		{
			Position = menuFechadoPos
		}
	)

	local logoTween = TweenService:Create(
		toggle,
		TweenInfo.new(
			0.25,
			Enum.EasingStyle.Back,
			Enum.EasingDirection.Out
		),
		{
			Size = UDim2.new(
				0,
				72,
				0,
				72
			)
		}
	)

	fechar:Play()
	logoTween:Play()

	fechar.Completed:Wait()

	menu.Visible = false
	animando = false

end

--========================================================--
-- 🖱️ CLIQUE NA LOGO
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
-- ❌ BOTÃO X
--========================================================--

closeButton.MouseButton1Click:Connect(function()

	fecharMenu()

end)

--========================================================--
-- 🖱️ LOGO ARRASTÁVEL
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
-- 🎖️ FIM DO SISTEMA
--========================================================--

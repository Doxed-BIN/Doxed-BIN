-- Create a ScreenGui to hold the GUI elements
local gui = Instance.new("ScreenGui")
gui.Name = "MyGui"
gui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- Create a button to interact with random chests
local button = Instance.new("TextButton")
button.Name = "RandomChestButton"
button.Text = "Gem Collector!"
button.Size = UDim2.new(0, 200, 0, 55)
button.Position = UDim2.new(0.5,550, 0.5, 125)
button.Parent = gui

-- Function to interact with random chests
local function interactWithRandomChests()
    for _, descendant in pairs(game.Workspace.RandomChests:GetDescendants()) do
        if descendant:IsA("Model") and string.match(descendant.Name, "Chest") then
            game.Players.LocalPlayer.Character:MoveTo(descendant.HumanoidRootPart.Position)
            wait(1)
            fireproximityprompt(descendant.HumanoidRootPart.ProximityPrompt)
        end
    end
end

-- Connect the button click event to the interaction function
button.MouseButton1Click:Connect(interactWithRandomChests)

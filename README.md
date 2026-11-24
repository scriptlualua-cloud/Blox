local a=game:GetService("Players")local b=game:GetService("RunService")local c=game:GetService("UserInputService")
local d=game:GetService("TweenService")local e=game:GetService("Workspace")local f=game:GetService("ReplicatedStorage")
local g=game:GetService("HttpService")local h=a.LocalPlayer;
local i,j,k,l=UDim2.new,UDim2.fromOffset,Vector3.new,Color3.fromRGB;
local function m()return h.Character end;
local n,o=task.wait,task.spawn;
local p=Enum.UserInputType.MouseMovement;
local q,r=Enum.Font.GothamBold,Enum.TextXAlignment.Left;
local s,t=Enum.UserInputType.Touch,Enum.UserInputType.MouseButton1;
if _G.HubBlox and _G.HubBlox.stop then pcall(_G.HubBlox.stop)end;
local u={running=true}_G.HubBlox=u;
pcall(function()if _G.hubAimFly_Close then _G.hubAimFly_Close()end end)local v=400;
local w={delay={0.01,1},forcaTurbo={1,10000},forcaPulo={1,5000},velFly={1,100000},altura={-100000,100000},alcance={0,1000000000}}
local x="hub_bloxfruits_v6.json"local y={player=true,npc=true,delay=0.08,turboOn=false,forcaTurbo=100,inf=false,forcaPulo=50,v3=true,v4=true,bot=false,fly=false,alvo="player",velFly=100,altura=0,alcance=0,parado=true,miraOn=true,orbs=true,cadeado=false,botX=20,botY=160,flyX=20,flyY=240}
local z=2.2;
local A=26;
local function B()pcall(function()if writefile then writefile(x,g:JSONEncode(y))end end)end;
pcall(function()if isfile and readfile and isfile(x)then local C=g:JSONDecode(readfile(x))for D,E in pairs(C)do if y[D]~=nil and type(E)==type(y[D])
then y[D]=E end end end end)y.bot,y.fly=false,false;
if y.alvo~="npc"then y.alvo="player"end;
local F={}local function G(H,I)local J=H:Connect(I)table.insert(F,J)return J end;
local K={}local function L(M,I)K[M]=K[M]or{}table.insert(K[M],I)end;
local function N(M)for O,I in ipairs(K[M]or{})do pcall(I)end end;
local function P(Q,I)local R,S=pcall(I)if not R then warn("[HubBlox] erro em "..Q..": "..tostring(S))end end;
local function T(U)return U and U:FindFirstChildOfClass("Humanoid")end;
local function V(U)return U and(U:FindFirstChild("HumanoidRootPart")or U.PrimaryPart)end;
local function W(U)local X=T(U)return X~=nil and X.Health>0 end;
local function Y()pcall(function()local Z=V(m())if Z then local _,a0=Z:FindFirstChild("TurboLV"),Z:FindFirstChild("TurboAtt")
if _ then _:Destroy()end;
if a0 then a0:Destroy()end end end)end;
Y()local a1;
local a2=Instance.new("ScreenGui")a2.Name="HubBlox"a2.ResetOnSpawn=false;
a2.IgnoreGuiInset=true;
a2.DisplayOrder=999;
local a3=pcall(function()a2.Parent=gethui and gethui()or game:GetService("CoreGui")end)if not a3 or not a2.Parent then a2.Parent=h:WaitForChild("PlayerGui")
end;
u.gui=a2;
local a4=l(8,8,8)local a5=l(22,22,22)local a6=l(235,235,235)local a7=l(55,55,55)local a8=Color3.new(1,1,1)local function a9(J,aa,ab)
local ac=Instance.new(J)for D,E in pairs(aa)do ac[D]=E end;
ac.Parent=ab;
return ac end;
local function ad(ae,Z)a9("UICorner",{CornerRadius=UDim.new(0,Z or 8)},ae)end;
local af,ag,ah=300,420,36;
local ai=a9("Frame",{Size=j(af,ag),Position=i(0.5,-af/2,0.15,0),BackgroundColor3=a4,BackgroundTransparency=.08,Active=true},a2)
ad(ai,12)a9("UIStroke",{Color=a6,Thickness=1.5},ai)local aj=a9("Frame",{Size=i(1,0,0,ah),BackgroundColor3=a5},ai)
ad(aj,12)a9("TextLabel",{Size=i(1,-90,1,0),Position=i(0,12,0,0),BackgroundTransparency=1,Text="👾 BLOX FRUITS HUB",TextColor3=a8,Font=q,TextSize=15,TextXAlignment=r},aj)
local function ak(al,am,an)local a0=a9("TextButton",{Size=j(28,24),Position=i(1,am,0.5,-12),BackgroundColor3=an,Text=al,TextColor3=a8,Font=q,TextSize=16},aj)
ad(a0,6)return a0 end;
local ao,ap=ak("-",-68,a7),ak("X",-36,a7)local aq=a9("ScrollingFrame",{Size=i(1,-12,1,-50),Position=i(0,6,0,44),BackgroundTransparency=1,BorderSizePixel=0,ScrollBarThickness=4,CanvasSize=i(),AutomaticCanvasSize=Enum.AutomaticSize.Y},ai)
a9("UIListLayout",{Padding=UDim.new(0,5),SortOrder=Enum.SortOrder.LayoutOrder},aq)do local ar,as,at;
G(aj.InputBegan,function(ac)if ac.UserInputType==s or ac.UserInputType==t then ar,as,at=true,ac.Position,ai.Position end end)
G(c.InputChanged,function(ac)if ar and(ac.UserInputType==s or ac.UserInputType==p)then local au=ac.Position-as;
ai.Position=i(at.X.Scale,at.X.Offset+au.X,at.Y.Scale,at.Y.Offset+au.Y)end end)G(c.InputEnded,function(ac)if ac.UserInputType==s or ac.UserInputType==t then ar=false end end)
end;
local function av(aw)a9("TextLabel",{Size=i(1,-8,0,20),BackgroundTransparency=1,Text="— "..aw.." —",TextColor3=a6,Font=q,TextSize=13},aq)
end;
local function ax(al,M)local a0=a9("TextButton",{Size=i(1,-8,0,34),BackgroundColor3=a5,Text="",AutoButtonColor=false},aq)
ad(a0)a9("TextLabel",{Size=i(1,-60,1,0),Position=i(0,10,0,0),BackgroundTransparency=1,Text=al,TextColor3=a8,Font=Enum.Font.Gotham,TextSize=14,TextXAlignment=r},a0)
local ay=a9("Frame",{Size=j(38,18),Position=i(1,-48,.5,-9),BackgroundColor3=a7},a0)ad(ay,9)local az=a9("Frame",{Size=j(14,14),Position=i(0,2,.5,-7),BackgroundColor3=a8},ay)
ad(az,7)local function aA()d:Create(ay,TweenInfo.new(.15),{BackgroundColor3=y[M]and a6 or a7}):Play()d:Create(az,TweenInfo.new(.15),{Position=y[M]
and i(1,-16,.5,-7)or i(0,2,.5,-7),BackgroundColor3=y[M]and a4 or a8}):Play()end;
aA()L(M,aA)G(a0.MouseButton1Click,function()y[M]=not y[M]N(M)B()end)end;
local function aB(al,M,aC,aD)local aE,aF=w[M][1],w[M][2]local aG=1;
local aH=a9("Frame",{Size=i(1,-8,0,74),BackgroundColor3=a5},aq)ad(aH)a9("TextLabel",{Size=i(1,-90,0,24),Position=i(0,10,0,2),BackgroundTransparency=1,Text=al,TextColor3=l(190,190,205),Font=Enum.Font.Gotham,TextSize=12,TextXAlignment=r},aH)
local aI=a9("TextButton",{Size=j(76,22),Position=i(1,-84,0,4),BackgroundColor3=a7,TextColor3=a8,Font=q,TextSize=11},aH)
ad(aI,6)local function aJ(aw,aK)local a0=a9("TextButton",{Size=j(46,34),Position=aK,BackgroundColor3=a7,Text=aw,TextColor3=a8,Font=q,TextSize=20},aH)
ad(a0,6)return a0 end;
local aL=aJ("-",i(0,10,0,32))local aM=aJ("+",i(1,-56,0,32))local aN=a9("TextBox",{Size=i(1,-124,0,34),Position=i(0,62,0,32),BackgroundColor3=a4,TextColor3=a6,Font=q,TextSize=20,ClearTextOnFocus=false,PlaceholderText="valor",Text=""},aH)
ad(aN,6)a9("UIStroke",{Color=a6,Thickness=1,Transparency=.5},aN)local function aO()aN.Text=string.format(aD,y[M])
aI.Text="passo "..tostring(aC[aG])end;
local function aP(E)E=math.floor(E*10000+0.5)/10000;
y[M]=math.clamp(E,aE,aF)aO()B()end;
G(aL.MouseButton1Click,function()aP(y[M]-aC[aG])end)G(aM.MouseButton1Click,function()aP(y[M]+aC[aG])end)G(aI.MouseButton1Click,function()
aG=aG%#aC+1;
aO()end)G(aN.FocusLost,function()local aQ=tonumber(aN.Text)if aQ then aP(aQ)else aO()end end)aO()end;
local function aR(al,M,aS,aT)local a0=a9("TextButton",{Size=i(1,-8,0,34),BackgroundColor3=a5,Text="",AutoButtonColor=false},aq)
ad(a0)local aU=a9("TextLabel",{Size=i(1,-20,1,0),Position=i(0,10,0,0),BackgroundTransparency=1,Text="",TextColor3=a8,Font=q,TextSize=14,TextXAlignment=r},a0)
local function aO()for ac,E in ipairs(aS)do if y[M]==E then aU.Text=al..": "..aT[ac]end end end;
aO()L(M,aO)G(a0.MouseButton1Click,function()local aV=1;
for ac,E in ipairs(aS)do if y[M]==E then aV=ac end end;
y[M]=aS[aV%#aS+1]N(M)B()end)end;
P("menu",function()av("COMBATE")ax("Bater em Players","player")ax("Bater em NPCs","npc")aB("Velocidade do ataque","delay",{0.01,0.05,0.1},"%.2f")
av("MOVIMENTO")ax("Turbo Impulso","turboOn")aB("Velocidade do Turbo","forcaTurbo",{1,10,100},"%g")ax("Pulo infinito","inf")
aB("Força do Pulo","forcaPulo",{1,10,100},"%g")av("RAÇA")ax("V3 automático (remote)","v3")ax("V4 automático (remote)","v4")
av("MIRA E VOO")ax("BOT (trava no alvo)","bot")ax("FLY (voa até o alvo)","fly")aR("Alvo","alvo",{"player","npc"},{"PLAYER","NPC"})
aB("Velocidade do FLY","velFly",{1,10,100},"%g")aB("Altura do FLY (- = abaixo)","altura",{1,10,100},"%g")aB("Distância de busca (0 = qualquer)","alcance",{1,10,100},"%g")
ax("Parado no ar sem alvo","parado")ax("Bolinha da mira","miraOn")ax("Bolinhas BOT/FLY na tela","orbs")ax("Cadeado das bolinhas","cadeado")
end)local aW=a9("TextButton",{Size=j(46,46),Position=i(0,12,0.5,0),BackgroundColor3=a4,BackgroundTransparency=.05,Text="👾",TextSize=22,Visible=false,AutoButtonColor=false},a2)
ad(aW,23)a9("UIStroke",{Color=a8,Thickness=1.5,Transparency=.3},aW)local aX=false;
G(ao.MouseButton1Click,function()aX=not aX;
aq.Visible=not aX;
ai.Size=aX and j(af,ah)or j(af,ag)ao.Text=aX and"+"or"-"end)G(ap.MouseButton1Click,function()ai.Visible=false;
aW.Visible=true end)do local ar,as,at,aY=false,nil,nil,0;
G(aW.InputBegan,function(ac)if ac.UserInputType==s or ac.UserInputType==t then ar,as,at,aY=true,ac.Position,aW.Position,0;
ac.Changed:Connect(function()if ac.UserInputState==Enum.UserInputState.End then ar=false;
if aY<8 then ai.Visible=true;
aW.Visible=false end end end)end end)G(c.InputChanged,function(ac)if ar and(ac.UserInputType==s or ac.UserInputType==p)
then local au=ac.Position-as;
aY=math.max(aY,au.Magnitude)aW.Position=i(at.X.Scale,at.X.Offset+au.X,at.Y.Scale,at.Y.Offset+au.Y)end end)end;
P("mira e bolinhas",function()do local aZ=a9("Frame",{Name="MiraDot",AnchorPoint=Vector2.new(0.5,0.5),Size=j(4,4),Position=i(0.5,0,0.5,-A),BackgroundColor3=a8,BorderSizePixel=0,Active=false,ZIndex=10,Visible=y.miraOn},a2)
ad(aZ,2)a9("UIStroke",{Color=Color3.new(0,0,0),Thickness=1,ApplyStrokeMode=Enum.ApplyStrokeMode.Border},aZ)L("miraOn",function()
aZ.Visible=y.miraOn end)end;
do local a_=64;
local b0=l(150,150,150)local function b1(am,b2)local R,b3=pcall(function()return e.CurrentCamera.ViewportSize end)
if R and b3 and b3.X>0 and b3.Y>0 then am=math.max(0,math.min(am,b3.X-a_))b2=math.max(0,math.min(b2,b3.Y-a_))end;
return am,b2 end;
local function b4(al,M,b5,b6)local am,b2=b1(y[b5],y[b6])local ae=a9("TextButton",{Size=j(a_,a_),Position=j(am,b2),BackgroundColor3=a4,BackgroundTransparency=.35,Text=al,TextColor3=b0,Font=q,TextSize=16,AutoButtonColor=false,Visible=y.orbs},a2)
ad(ae,a_/2)local b7=a9("UIStroke",{Color=b0,Thickness=1},ae)local function b8()local b9=y[M]ae.BackgroundTransparency=b9 and.05 or.35;
ae.TextColor3=b9 and a8 or b0;
b7.Color=b9 and a8 or b0;
b7.Thickness=b9 and 3 or 1 end;
b8()L(M,b8)L("orbs",function()ae.Visible=y.orbs end)local ar,as,at,aY,ba=false,nil,nil,0,nil;
G(ae.InputBegan,function(ac)if ac.UserInputType==s or ac.UserInputType==t then ar,as,at,aY,ba=true,ac.Position,ae.Position,0,ac end end)
G(c.InputChanged,function(ac)if not ar then return end;
local bb=ac.UserInputType==p or ac.UserInputType==s and ac==ba;
if not bb then return end;
local au=ac.Position-as;
aY=math.max(aY,au.Magnitude)if aY>=8 and not y.cadeado then ae.Position=i(at.X.Scale,at.X.Offset+au.X,at.Y.Scale,at.Y.Offset+au.Y)
end end)G(c.InputEnded,function(ac)if not ar then return end;
local bc=ac==ba or ac.UserInputType==t and ba and ba.UserInputType==t;
if not bc then return end;
ar=false;
if aY<8 then y[M]=not y[M]N(M)elseif not y.cadeado then y[b5],y[b6]=ae.Position.X.Offset,ae.Position.Y.Offset;
B()end end)end;
b4("BOT","bot","botX","botY")b4("FLY","fly","flyX","flyY")end end)u.stop=function()u.running=false;
pcall(function()b:UnbindFromRenderStep("HubBloxAim")end)for O,J in ipairs(F)do pcall(function()J:Disconnect()end)
end;
pcall(a1)Y()pcall(function()a2:Destroy()end)end;
P("combate e raca",function()local bd,be,bf,bg;
o(function()pcall(function()bd=f:WaitForChild("Remotes",15):WaitForChild("CommF_",15)local bh=f:WaitForChild("Modules",15):WaitForChild("Net",15)
be=bh:WaitForChild("RE/RegisterAttack",15)bf=bh:WaitForChild("RE/RegisterHit",15)end)pcall(function()bg=f:WaitForChild("Remotes",15):WaitForChild("CommE",15)
end)end)local function bi()local bj,bk,bl={},nil,v;
local bm=V(m())if not bm then return bj,nil end;
local function bn(bo)local bp=V(bo)if not bp or not W(bo)then return end;
local au=(bp.Position-bm.Position).Magnitude;
if au>v then return end;
table.insert(bj,{bo,bo:FindFirstChild("Head")or bp})if au<=bl then bk,bl=bp,au end end;
if y.npc then local bq=e:FindFirstChild("Enemies")if bq then for O,br in ipairs(bq:GetChildren())do bn(br)end end end;
if y.player then for O,aa in ipairs(a:GetPlayers())do if aa~=h and aa.Character then bn(aa.Character)end end end;
return bj,bk end;
o(function()while u.running do local J=m()if bd and J and W(J)and not J:FindFirstChild("HasBuso")then pcall(function()
bd:InvokeServer("Buso")end)end;
n(1)end end)o(function()while u.running do local J=m()local bs=J and J:FindFirstChildOfClass("Tool")if bs and W(J)
and(y.player or y.npc)then local bt,bk=bi()if#bt>0 then if be then pcall(function()be:FireServer(0.40000000596046448,1)
end)end;
if bf then pcall(function()bf:FireServer(bt[1][2],bt)end)end;
local bu=bs:FindFirstChild("LeftClickRemote")local bm=V(J)if bu and bu:IsA("RemoteEvent")and bk and bm then local bv=k(bk.Position.X-bm.Position.X,0,bk.Position.Z-bm.Position.Z)
if bv.Magnitude>0 then pcall(function()bu:FireServer(bv.Unit,1)end)end end end end;
n(math.max(y.delay,w.delay[1]))end end)o(function()n(1)while u.running do local J=m()if y.v3 and bg and J and W(J)
then pcall(function()bg:FireServer("ActivateAbility")end)n(0.5)else n(0.2)end end end)o(function()while u.running do local J=m()
local bw=J and J:FindFirstChild("RaceEnergy")local bx=J and J:FindFirstChild("RaceTransformed")if y.v4 and bw and bx and bw.Value>=1 and not bx.Value and W(J)
then local by=h:FindFirstChild("Backpack")local bs=by and by:FindFirstChild("Awakening")or J:FindFirstChild("Awakening")
local bz=bs and bs:FindFirstChild("RemoteFunction")if bz then pcall(function()bz:InvokeServer(true)end)end end;
n(0.1)end end)end)P("turbo e pulo",function()local bA=RaycastParams.new()bA.FilterType=Enum.RaycastFilterType.Exclude;
bA.RespectCanCollide=true;
local function bB(bC)local bD=bC:FindFirstChild("TurboLV")if bD then return bD end;
local bE=Instance.new("Attachment")bE.Name="TurboAtt"bE.Parent=bC;
bD=Instance.new("LinearVelocity")bD.Name="TurboLV"bD.Attachment0=bE;
bD.RelativeTo=Enum.ActuatorRelativeTo.World;
bD.VelocityConstraintMode=Enum.VelocityConstraintMode.Vector;
bD.ForceLimitMode=Enum.ForceLimitMode.PerAxis;
bD.MaxAxesForce=k(1e9,0,1e9)bD.VectorVelocity=Vector3.zero;
bD.Parent=bC;
return bD end;
local function bF(bC,bv,bG,bH)bA.FilterDescendantsInstances={m()}local bI=math.min(bH,1/20)local bJ=bG*bI*2+z;
local bK=bG;
for O,bL in ipairs({-1,0.5,2})do local bM=bC.Position+k(0,bL,0)local Z=e:Raycast(bM,bv*bJ,bA)if Z then local bN=math.max(0,(Z.Distance-z)/(bI*2))
bK=math.min(bK,bN)end end;
return bK end;
local bO=0;
local function bP()if not y.inf then return end;
local bQ=os.clock()if bQ-bO<0.12 then return end;
bO=bQ;
local bR=m()local X,Z=T(bR),V(bR)if not X or not Z or X.Health<=0 then return end;
X:ChangeState(Enum.HumanoidStateType.Jumping)local E=Z.AssemblyLinearVelocity;
Z.AssemblyLinearVelocity=k(E.X,y.forcaPulo,E.Z)end;
G(c.JumpRequest,bP)G(b.Heartbeat,function(bH)local bR=m()local X,Z=T(bR),V(bR)if not X or not Z then return end;
if y.inf and X.Jump then bP()end;
if not y.turboOn then local bS=Z:FindFirstChild("TurboLV")if bS then bS.Enabled=false end else local bD=bB(Z)bD.Enabled=true;
local U=X.MoveDirection;
local bT=k(U.X,0,U.Z)if bT.Magnitude<0.1 then bD.VectorVelocity=Vector3.zero else local bv=bT.Unit;
bD.VectorVelocity=bv*bF(Z,bv,y.forcaTurbo,bH)end end end)end)P("mira e voo",function()local bU=0.4;
local bV={t=nil,n=0,s=nil,c={},h=nil,p={},q=-100}local function bW(bX,bY)if CFrame.lookAt then return CFrame.lookAt(bX,bY)
end;
return CFrame.new(bX,bY)end;
local function bZ(U)return U~=nil and U.Parent~=nil and W(U)and V(U)~=nil end;
local function b_()local bQ=os.clock()if bQ-bV.q<1 then return bV.p end;
bV.q=bQ;
local c0={}local function bn(U)if U and U:IsA("Model")and U~=m()and a:GetPlayerFromCharacter(U)==nil and bZ(U)then table.insert(c0,U)
end end;
local bq=e:FindFirstChild("Enemies")if bq then for O,U in ipairs(bq:GetChildren())do bn(U)end else for O,au in ipairs(e:GetDescendants())
do if au:IsA("Humanoid")then bn(au.Parent)end end end;
bV.p=c0;
return c0 end;
local function c1()local c2=V(m())if not c2 then return nil end;
local c3={}if y.alvo=="npc"then c3=b_()else for O,aa in ipairs(a:GetPlayers())do if aa~=h and aa.Character and bZ(aa.Character)
then table.insert(c3,aa.Character)end end end;
local c4,c5;
for O,U in ipairs(c3)do if bZ(U)then local au=(V(U).Position-c2.Position).Magnitude;
if(y.alcance==0 or au<=y.alcance)and(not c5 or au<c5)then c4,c5=U,au end end end;
return c4 end;
local function c6(b9)if b9 then local bR=m()if not bR then return end;
for O,au in ipairs(bR:GetDescendants())do if au:IsA("BasePart")then if bV.c[au]==nil then bV.c[au]=au.CanCollide end;
au.CanCollide=false end end else for c7,c8 in pairs(bV.c)do if c7 and c7.Parent then c7.CanCollide=c8 end;
bV.c[c7]=nil end end end;
a1=function()if bV.s then local X=bV.s.hum;
if X and X.Parent then X.AutoRotate=bV.s.autoRotate;
X.PlatformStand=bV.s.platformStand end;
bV.s=nil end;
c6(false)bV.h=nil;
bV.t=nil end;
L("alvo",function()bV.t=nil;
bV.n=0 end)local function c9(bH)if not(y.bot or y.fly)then if bV.s or next(bV.c)~=nil then a1()end;
return end;
if not y.fly and next(bV.c)~=nil then c6(false)end;
if bV.t and y.alcance>0 then local ca,bx=V(m()),V(bV.t)if ca and bx and(bx.Position-ca.Position).Magnitude>y.alcance then bV.t=nil end end;
if not bZ(bV.t)then bV.t=nil;
if os.clock()>=bV.n then bV.t=c1()if not bV.t then bV.n=os.clock()+0.3 end end end;
if not bV.t then if y.fly and y.parado then local J=m()local Z,X=V(J),T(J)if Z and X and X.Health>0 then if not bV.s or bV.s.hum~=X then bV.s={hum=X,autoRotate=X.AutoRotate,platformStand=X.PlatformStand}
end;
X.PlatformStand=true;
if not bV.h then bV.h=Z.CFrame end;
Z.AssemblyLinearVelocity=k(0,0,0)Z.AssemblyAngularVelocity=k(0,0,0)Z.CFrame=bV.h end else bV.h=nil end;
return end;
bV.h=nil;
local bR=m()local bm,cb=V(bR),T(bR)if not bm or not cb or cb.Health<=0 then return end;
if not bV.s or bV.s.hum~=cb then bV.s={hum=cb,autoRotate=cb.AutoRotate,platformStand=cb.PlatformStand}end;
cb.AutoRotate=false;
cb.PlatformStand=y.fly;
local cc=V(bV.t)local cd=cc.Position;
local ce=bm.Position;
if y.fly then bm.AssemblyLinearVelocity=k(0,0,0)bm.AssemblyAngularVelocity=k(0,0,0)local cf=cc.CFrame.LookVector;
local cg=k(cf.X,0,cf.Z)if cg.Magnitude<0.01 then cg=k(0,0,-1)else cg=cg.Unit end;
local ch=cd-cg*bU+k(0,y.altura,0)local bY=ch-bm.Position;
local ci=bY.Magnitude;
local cj=y.velFly*bH;
if cj~=cj then cj=0 end;
if ci<0.05 or ci<=cj then ce=ch else ce=bm.Position+bY.Unit*cj end end;
local ck=k(cd.X,ce.Y,cd.Z)if(ck-ce).Magnitude>0.05 then bm.CFrame=bW(ce,ck)else bm.CFrame=CFrame.new(ce)*(bm.CFrame-bm.CFrame.Position)
end;
local cl=e.CurrentCamera;
if cl then local cm=cl.CFrame.Position;
if(cd-cm).Magnitude>0.05 then local cn=bW(cm,cd)local co=cl.ViewportSize.Y;
if co>0 then local cp=math.atan(A/(co/2)*math.tan(math.rad(cl.FieldOfView)/2))cn=cn*CFrame.Angles(-cp,0,0)end;
cl.CFrame=cn end end end;
local function cq(bH)if not u.running then return end;
local R,S=pcall(c9,bH)if not R then warn("[HubBlox] "..tostring(S))end end;
if not pcall(function()b:BindToRenderStep("HubBloxAim",Enum.RenderPriority.Camera.Value+1,cq)end)then G(b.RenderStepped,cq)
end;
G(b.Stepped,function()if y.fly then pcall(c6,true)end end)end)print("[HubBlox] carregado")

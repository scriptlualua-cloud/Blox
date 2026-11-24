local a=game:GetService("Players")local b=game:GetService("RunService")local c=game:GetService("UserInputService")
local d=game:GetService("TweenService")local e=game:GetService("Workspace")local f=game:GetService("ReplicatedStorage")
local g=game:GetService("HttpService")local h=a.LocalPlayer;
local i,j,k,l=UDim2.new,UDim2.fromOffset,Vector3.new,Color3.fromRGB;
local function m()return h.Character end;
local n,o=task.wait,task.spawn;
local p=Enum.UserInputType.MouseMovement;
local q,r=Enum.Font.GothamBold,Enum.TextXAlignment.Left;
local s,t=Enum.UserInputType.Touch,Enum.UserInputType.MouseButton1;
local function u(v)local w=v.UserInputType;
return w==s or w==t end;
local function x(v)local w=v.UserInputType;
return w==s or w==p end;
if _G.HubBlox and _G.HubBlox.stop then pcall(_G.HubBlox.stop)end;
local y={running=true}_G.HubBlox=y;
pcall(function()if _G.hubAimFly_Close then _G.hubAimFly_Close()end end)local z=400;
local A={delay={0.01,1},forcaTurbo={1,10000},forcaPulo={1,5000},velFly={1,100000},altura={-100000,100000},alcance={0,1000000000},antlim={1,500}}
local B="hub_bloxfruits_v6.json"local C={player=true,npc=true,delay=0.08,turboOn=false,forcaTurbo=100,inf=false,forcaPulo=50,v3=true,v4=true,bot=false,fly=false,alvo="player",velFly=100,altura=0,alcance=0,ant=false,antecipa=2,antlim=30,parado=true,miraOn=true,orbs=true,cadeado=false,botX=20,botY=160,flyX=20,flyY=240}
local D=2.2;
local E=26;
local function F()pcall(function()if writefile then writefile(B,g:JSONEncode(C))end end)end;
pcall(function()if isfile and readfile and isfile(B)then local G=g:JSONDecode(readfile(B))for H,I in pairs(G)do if C[H]~=nil and type(I)==type(C[H])
then C[H]=I end end end end)C.bot,C.fly=false,false;
if C.alvo~="npc"then C.alvo="player"end;
local J={}local function K(L,M)local N=L:Connect(M)table.insert(J,N)return N end;
local O={}local function P(Q,M)O[Q]=O[Q]or{}table.insert(O[Q],M)end;
local function R(Q)for S,M in ipairs(O[Q]or{})do pcall(M)end end;
local function T(U,M)local V,W=pcall(M)if not V then warn("[HubBlox] erro em "..U..": "..tostring(W))end end;
local function X(Y)return Y and Y:FindFirstChildOfClass("Humanoid")end;
local function Z(Y)return Y and(Y:FindFirstChild("HumanoidRootPart")or Y.PrimaryPart)end;
local function _(Y)local a0=X(Y)return a0~=nil and a0.Health>0 end;
local function a1()pcall(function()local a2=Z(m())if a2 then local a3,a4=a2:FindFirstChild("TurboLV"),a2:FindFirstChild("TurboAtt")
if a3 then a3:Destroy()end;
if a4 then a4:Destroy()end end end)end;
a1()local a5;
local a6=Instance.new("ScreenGui")a6.Name="HubBlox"a6.ResetOnSpawn=false;
a6.IgnoreGuiInset=true;
a6.DisplayOrder=999;
local a7=pcall(function()a6.Parent=gethui and gethui()or game:GetService("CoreGui")end)if not a7 or not a6.Parent then a6.Parent=h:WaitForChild("PlayerGui")
end;
y.gui=a6;
local a8=l(8,8,8)local a9=l(22,22,22)local aa=l(235,235,235)local ab=l(55,55,55)local ac=Color3.new(1,1,1)local function ad(N,ae,af)
local v=Instance.new(N)for H,I in pairs(ae)do v[H]=I end;
v.Parent=af;
return v end;
local function ag(ah,a2)ad("UICorner",{CornerRadius=UDim.new(0,a2 or 8)},ah)end;
local ai,aj,ak=300,420,36;
local al=ad("Frame",{Size=j(ai,aj),Position=i(0.5,-ai/2,0.15,0),BackgroundColor3=a8,BackgroundTransparency=.08,Active=true},a6)
ag(al,12)ad("UIStroke",{Color=aa,Thickness=1.5},al)local am=ad("Frame",{Size=i(1,0,0,ak),BackgroundColor3=a9},al)
ag(am,12)ad("TextLabel",{Size=i(1,-90,1,0),Position=i(0,12,0,0),BackgroundTransparency=1,Text="👾 BLOX FRUITS HUB",TextColor3=ac,Font=q,TextSize=15,TextXAlignment=r},am)
local function an(ao,ap,aq)local a4=ad("TextButton",{Size=j(28,24),Position=i(1,ap,0.5,-12),BackgroundColor3=aq,Text=ao,TextColor3=ac,Font=q,TextSize=16},am)
ag(a4,6)return a4 end;
local ar,as=an("-",-68,ab),an("X",-36,ab)local at=ad("ScrollingFrame",{Size=i(1,-12,1,-50),Position=i(0,6,0,44),BackgroundTransparency=1,BorderSizePixel=0,ScrollBarThickness=4,CanvasSize=i(),AutomaticCanvasSize=Enum.AutomaticSize.Y},al)
ad("UIListLayout",{Padding=UDim.new(0,5),SortOrder=Enum.SortOrder.LayoutOrder},at)do local au,av,aw;
K(am.InputBegan,function(v)if u(v)then au,av,aw=true,v.Position,al.Position end end)K(c.InputChanged,function(v)
if au and x(v)then local ax=v.Position-av;
al.Position=i(aw.X.Scale,aw.X.Offset+ax.X,aw.Y.Scale,aw.Y.Offset+ax.Y)end end)K(c.InputEnded,function(v)if u(v)
then au=false end end)end;
local function ay(w)ad("TextLabel",{Size=i(1,-8,0,20),BackgroundTransparency=1,Text="— "..w.." —",TextColor3=aa,Font=q,TextSize=13},at)
end;
local function az(ao,Q)local a4=ad("TextButton",{Size=i(1,-8,0,34),BackgroundColor3=a9,Text="",AutoButtonColor=false},at)
ag(a4)ad("TextLabel",{Size=i(1,-60,1,0),Position=i(0,10,0,0),BackgroundTransparency=1,Text=ao,TextColor3=ac,Font=Enum.Font.Gotham,TextSize=14,TextXAlignment=r},a4)
local aA=ad("Frame",{Size=j(38,18),Position=i(1,-48,.5,-9),BackgroundColor3=ab},a4)ag(aA,9)local aB=ad("Frame",{Size=j(14,14),Position=i(0,2,.5,-7),BackgroundColor3=ac},aA)
ag(aB,7)local function aC()d:Create(aA,TweenInfo.new(.15),{BackgroundColor3=C[Q]and aa or ab}):Play()d:Create(aB,TweenInfo.new(.15),{Position=C[Q]
and i(1,-16,.5,-7)or i(0,2,.5,-7),BackgroundColor3=C[Q]and a8 or ac}):Play()end;
aC()P(Q,aC)K(a4.MouseButton1Click,function()C[Q]=not C[Q]R(Q)F()end)end;
local function aD(ao,Q,aE,aF)local aG,aH=A[Q][1],A[Q][2]local aI=1;
local aJ=ad("Frame",{Size=i(1,-8,0,74),BackgroundColor3=a9},at)ag(aJ)ad("TextLabel",{Size=i(1,-90,0,24),Position=i(0,10,0,2),BackgroundTransparency=1,Text=ao,TextColor3=l(190,190,205),Font=Enum.Font.Gotham,TextSize=12,TextXAlignment=r},aJ)
local aK=ad("TextButton",{Size=j(76,22),Position=i(1,-84,0,4),BackgroundColor3=ab,TextColor3=ac,Font=q,TextSize=11},aJ)
ag(aK,6)local function aL(w,aM)local a4=ad("TextButton",{Size=j(46,34),Position=aM,BackgroundColor3=ab,Text=w,TextColor3=ac,Font=q,TextSize=20},aJ)
ag(a4,6)return a4 end;
local aN=aL("-",i(0,10,0,32))local aO=aL("+",i(1,-56,0,32))local aP=ad("TextBox",{Size=i(1,-124,0,34),Position=i(0,62,0,32),BackgroundColor3=a8,TextColor3=aa,Font=q,TextSize=20,ClearTextOnFocus=false,PlaceholderText="valor",Text=""},aJ)
ag(aP,6)ad("UIStroke",{Color=aa,Thickness=1,Transparency=.5},aP)local function aQ()aP.Text=string.format(aF,C[Q])
aK.Text="passo "..tostring(aE[aI])end;
local function aR(I)I=math.floor(I*10000+0.5)/10000;
C[Q]=math.clamp(I,aG,aH)aQ()F()end;
K(aN.MouseButton1Click,function()aR(C[Q]-aE[aI])end)K(aO.MouseButton1Click,function()aR(C[Q]+aE[aI])end)K(aK.MouseButton1Click,function()
aI=aI%#aE+1;
aQ()end)K(aP.FocusLost,function()local aS=tonumber(aP.Text)if aS then aR(aS)else aQ()end end)aQ()end;
local function aT(ao,Q,aU,aV)local a4=ad("TextButton",{Size=i(1,-8,0,34),BackgroundColor3=a9,Text="",AutoButtonColor=false},at)
ag(a4)local aW=ad("TextLabel",{Size=i(1,-20,1,0),Position=i(0,10,0,0),BackgroundTransparency=1,Text="",TextColor3=ac,Font=q,TextSize=14,TextXAlignment=r},a4)
local function aQ()for v,I in ipairs(aU)do if C[Q]==I then aW.Text=ao..": "..aV[v]end end end;
aQ()P(Q,aQ)K(a4.MouseButton1Click,function()local aX=1;
for v,I in ipairs(aU)do if C[Q]==I then aX=v end end;
C[Q]=aU[aX%#aU+1]R(Q)F()end)end;
T("m",function()ay("COMBATE")az("Bater em Players","player")az("Bater em NPCs","npc")aD("Velocidade do ataque","delay",{0.01,0.05,0.1},"%.2f")
ay("MOVIMENTO")az("Turbo Impulso","turboOn")aD("Velocidade do Turbo","forcaTurbo",{1,10,100},"%g")az("Pulo infinito","inf")
aD("Força do Pulo","forcaPulo",{1,10,100},"%g")ay("RAÇA")az("V3 automático","v3")az("V4 automático","v4")ay("MIRA E VOO")
az("BOT (trava no alvo)","bot")az("FLY (voa até o alvo)","fly")aT("Alvo","alvo",{"player","npc"},{"PLAYER","NPC"})
aD("Velocidade do FLY","velFly",{1,10,100},"%g")aD("Altura do FLY (- = abaixo)","altura",{1,10,100},"%g")aD("Distância (0 = qualquer)","alcance",{1,10,100},"%g")
az("Antecipar movimento","ant")aD("Limite antecipação","antlim",{1,10,100},"%g")az("Parado no ar","parado")az("Bolinha da mira","miraOn")
az("Bolinhas na tela","orbs")az("Cadeado das bolinhas","cadeado")end)local aY=ad("TextButton",{Size=j(46,46),Position=i(0,12,0.5,0),BackgroundColor3=a8,BackgroundTransparency=.05,Text="👾",TextSize=22,Visible=false,AutoButtonColor=false},a6)
ag(aY,23)ad("UIStroke",{Color=ac,Thickness=1.5,Transparency=.3},aY)local aZ=false;
K(ar.MouseButton1Click,function()aZ=not aZ;
at.Visible=not aZ;
al.Size=aZ and j(ai,ak)or j(ai,aj)ar.Text=aZ and"+"or"-"end)K(as.MouseButton1Click,function()al.Visible=false;
aY.Visible=true end)do local au,av,aw,a_=false,nil,nil,0;
K(aY.InputBegan,function(v)if u(v)then au,av,aw,a_=true,v.Position,aY.Position,0;
v.Changed:Connect(function()if v.UserInputState==Enum.UserInputState.End then au=false;
if a_<8 then al.Visible=true;
aY.Visible=false end end end)end end)K(c.InputChanged,function(v)if au and x(v)then local ax=v.Position-av;
a_=math.max(a_,ax.Magnitude)aY.Position=i(aw.X.Scale,aw.X.Offset+ax.X,aw.Y.Scale,aw.Y.Offset+ax.Y)end end)end;
T("b",function()do local b0=ad("Frame",{Name="MiraDot",AnchorPoint=Vector2.new(0.5,0.5),Size=j(4,4),Position=i(0.5,0,0.5,-E),BackgroundColor3=ac,BorderSizePixel=0,Active=false,ZIndex=10,Visible=C.miraOn},a6)
ag(b0,2)ad("UIStroke",{Color=Color3.new(0,0,0),Thickness=1,ApplyStrokeMode=Enum.ApplyStrokeMode.Border},b0)P("miraOn",function()
b0.Visible=C.miraOn end)end;
do local b1=64;
local b2=l(150,150,150)local function b3(ap,b4)local V,b5=pcall(function()return e.CurrentCamera.ViewportSize end)
if V and b5 and b5.X>0 and b5.Y>0 then ap=math.max(0,math.min(ap,b5.X-b1))b4=math.max(0,math.min(b4,b5.Y-b1))end;
return ap,b4 end;
local function b6(ao,Q,b7,b8)local ap,b4=b3(C[b7],C[b8])local ah=ad("TextButton",{Size=j(b1,b1),Position=j(ap,b4),BackgroundColor3=a8,BackgroundTransparency=.35,Text=ao,TextColor3=b2,Font=q,TextSize=16,AutoButtonColor=false,Visible=C.orbs},a6)
ag(ah,b1/2)local b9=ad("UIStroke",{Color=b2,Thickness=1},ah)local function ba()local bb=C[Q]ah.BackgroundTransparency=bb and.05 or.35;
ah.TextColor3=bb and ac or b2;
b9.Color=bb and ac or b2;
b9.Thickness=bb and 3 or 1 end;
ba()P(Q,ba)P("orbs",function()ah.Visible=C.orbs end)local au,av,aw,a_,bc=false,nil,nil,0,nil;
K(ah.InputBegan,function(v)if u(v)then au,av,aw,a_,bc=true,v.Position,ah.Position,0,v end end)K(c.InputChanged,function(v)
if not au then return end;
local bd=v.UserInputType==p or v.UserInputType==s and v==bc;
if not bd then return end;
local ax=v.Position-av;
a_=math.max(a_,ax.Magnitude)if a_>=8 and not C.cadeado then ah.Position=i(aw.X.Scale,aw.X.Offset+ax.X,aw.Y.Scale,aw.Y.Offset+ax.Y)
end end)K(c.InputEnded,function(v)if not au then return end;
local be=v==bc or v.UserInputType==t and bc and bc.UserInputType==t;
if not be then return end;
au=false;
if a_<8 then C[Q]=not C[Q]R(Q)elseif not C.cadeado then C[b7],C[b8]=ah.Position.X.Offset,ah.Position.Y.Offset;
F()end end)end;
b6("BOT","bot","botX","botY")b6("FLY","fly","flyX","flyY")end end)y.stop=function()y.running=false;
pcall(function()b:UnbindFromRenderStep("HubBloxAim")end)for S,N in ipairs(J)do pcall(function()N:Disconnect()end)
end;
pcall(a5)a1()pcall(function()a6:Destroy()end)end;
T("c",function()local bf,bg,bh,bi;
o(function()pcall(function()bf=f:WaitForChild("Remotes",15):WaitForChild("CommF_",15)local bj=f:WaitForChild("Modules",15):WaitForChild("Net",15)
bg=bj:WaitForChild("RE/RegisterAttack",15)bh=bj:WaitForChild("RE/RegisterHit",15)end)pcall(function()bi=f:WaitForChild("Remotes",15):WaitForChild("CommE",15)
end)end)local function bk()local bl,bm,bn={},nil,z;
local bo=Z(m())if not bo then return bl,nil end;
local function bp(bq)local br=Z(bq)if not br or not _(bq)then return end;
local ax=(br.Position-bo.Position).Magnitude;
if ax>z then return end;
table.insert(bl,{bq,bq:FindFirstChild("Head")or br})if ax<=bn then bm,bn=br,ax end end;
if C.npc then local bs=e:FindFirstChild("Enemies")if bs then for S,bt in ipairs(bs:GetChildren())do bp(bt)end end end;
if C.player then for S,ae in ipairs(a:GetPlayers())do if ae~=h and ae.Character then bp(ae.Character)end end end;
return bl,bm end;
o(function()while y.running do local N=m()if bf and N and _(N)and not N:FindFirstChild("HasBuso")then pcall(function()
bf:InvokeServer("Buso")end)end;
n(1)end end)o(function()while y.running do local N=m()local bu=N and N:FindFirstChildOfClass("Tool")if bu and _(N)
and(C.player or C.npc)then local bv,bm=bk()if#bv>0 then if bg then pcall(function()bg:FireServer(0.40000000596046448,1)
end)end;
if bh then pcall(function()bh:FireServer(bv[1][2],bv)end)end;
local bw=bu:FindFirstChild("LeftClickRemote")local bo=Z(N)if bw and bw:IsA("RemoteEvent")and bm and bo then local bx=k(bm.Position.X-bo.Position.X,0,bm.Position.Z-bo.Position.Z)
if bx.Magnitude>0 then pcall(function()bw:FireServer(bx.Unit,1)end)end end end end;
n(math.max(C.delay,A.delay[1]))end end)o(function()n(1)while y.running do local N=m()if C.v3 and bi and N and _(N)
then pcall(function()bi:FireServer("ActivateAbility")end)n(0.5)else n(0.2)end end end)o(function()while y.running do local N=m()
local by=N and N:FindFirstChild("RaceEnergy")local bz=N and N:FindFirstChild("RaceTransformed")if C.v4 and by and bz and by.Value>=1 and not bz.Value and _(N)
then local bA=h:FindFirstChild("Backpack")local bu=bA and bA:FindFirstChild("Awakening")or N:FindFirstChild("Awakening")
local bB=bu and bu:FindFirstChild("RemoteFunction")if bB then pcall(function()bB:InvokeServer(true)end)end end;
n(0.1)end end)end)T("t",function()local bC=RaycastParams.new()bC.FilterType=Enum.RaycastFilterType.Exclude;
bC.RespectCanCollide=true;
local function bD(bE)local bF=bE:FindFirstChild("TurboLV")if bF then return bF end;
local bG=Instance.new("Attachment")bG.Name="TurboAtt"bG.Parent=bE;
bF=Instance.new("LinearVelocity")bF.Name="TurboLV"bF.Attachment0=bG;
bF.RelativeTo=Enum.ActuatorRelativeTo.World;
bF.VelocityConstraintMode=Enum.VelocityConstraintMode.Vector;
bF.ForceLimitMode=Enum.ForceLimitMode.PerAxis;
bF.MaxAxesForce=k(1e9,0,1e9)bF.VectorVelocity=Vector3.zero;
bF.Parent=bE;
return bF end;
local function bH(bE,bx,bI,bJ)bC.FilterDescendantsInstances={m()}local bK=math.min(bJ,1/20)local bL=bI*bK*2+D;
local bM=bI;
for S,bN in ipairs({-1,0.5,2})do local bO=bE.Position+k(0,bN,0)local a2=e:Raycast(bO,bx*bL,bC)if a2 then local bP=math.max(0,(a2.Distance-D)/(bK*2))
bM=math.min(bM,bP)end end;
return bM end;
local bQ=0;
local function bR()if not C.inf then return end;
local bS=os.clock()if bS-bQ<0.12 then return end;
bQ=bS;
local bT=m()local a0,a2=X(bT),Z(bT)if not a0 or not a2 or a0.Health<=0 then return end;
a0:ChangeState(Enum.HumanoidStateType.Jumping)local I=a2.AssemblyLinearVelocity;
a2.AssemblyLinearVelocity=k(I.X,C.forcaPulo,I.Z)end;
K(c.JumpRequest,bR)K(b.Heartbeat,function(bJ)local bT=m()local a0,a2=X(bT),Z(bT)if not a0 or not a2 then return end;
if C.inf and a0.Jump then bR()end;
if not C.turboOn then local bU=a2:FindFirstChild("TurboLV")if bU then bU.Enabled=false end else local bF=bD(a2)
bF.Enabled=true;
local Y=a0.MoveDirection;
local bV=k(Y.X,0,Y.Z)if bV.Magnitude<0.1 then bF.VectorVelocity=Vector3.zero else local bx=bV.Unit;
bF.VectorVelocity=bx*bH(a2,bx,C.forcaTurbo,bJ)end end end)end)T("v",function()local bW=0.4;
local bX={t=nil,n=0,s=nil,c={},h=nil,p={},q=-100}local function bY(bZ,b_)if CFrame.lookAt then return CFrame.lookAt(bZ,b_)
end;
return CFrame.new(bZ,b_)end;
local function c0(Y)return Y~=nil and Y.Parent~=nil and _(Y)and Z(Y)~=nil end;
local function c1()local bS=os.clock()if bS-bX.q<1 then return bX.p end;
bX.q=bS;
local c2={}local function bp(Y)if Y and Y:IsA("Model")and Y~=m()and a:GetPlayerFromCharacter(Y)==nil and c0(Y)then table.insert(c2,Y)
end end;
local bs=e:FindFirstChild("Enemies")if bs then for S,Y in ipairs(bs:GetChildren())do bp(Y)end else for S,ax in ipairs(e:GetDescendants())
do if ax:IsA("Humanoid")then bp(ax.Parent)end end end;
bX.p=c2;
return c2 end;
local function c3()local c4=Z(m())if not c4 then return nil end;
local c5={}if C.alvo=="npc"then c5=c1()else for S,ae in ipairs(a:GetPlayers())do if ae~=h and ae.Character and c0(ae.Character)
then table.insert(c5,ae.Character)end end end;
local c6,c7;
for S,Y in ipairs(c5)do if c0(Y)then local ax=(Z(Y).Position-c4.Position).Magnitude;
if(C.alcance==0 or ax<=C.alcance)and(not c7 or ax<c7)then c6,c7=Y,ax end end end;
return c6 end;
local function c8(bb)if bb then local bT=m()if not bT then return end;
for S,ax in ipairs(bT:GetDescendants())do if ax:IsA("BasePart")then if bX.c[ax]==nil then bX.c[ax]=ax.CanCollide end;
ax.CanCollide=false end end else for c9,ca in pairs(bX.c)do if c9 and c9.Parent then c9.CanCollide=ca end;
bX.c[c9]=nil end end end;
a5=function()if bX.s then local a0=bX.s.hum;
if a0 and a0.Parent then a0.AutoRotate=bX.s.autoRotate;
a0.PlatformStand=bX.s.platformStand end;
bX.s=nil end;
c8(false)bX.h=nil;
bX.t=nil end;
P("alvo",function()bX.t=nil;
bX.n=0 end)local function cb(bJ)if not(C.bot or C.fly)then if bX.s or next(bX.c)~=nil then a5()end;
return end;
if not C.fly and next(bX.c)~=nil then c8(false)end;
if bX.t and C.alcance>0 then local cc,bz=Z(m()),Z(bX.t)if cc and bz and(bz.Position-cc.Position).Magnitude>C.alcance then bX.t=nil end end;
if not c0(bX.t)then bX.t=nil;
if os.clock()>=bX.n then bX.t=c3()if not bX.t then bX.n=os.clock()+0.3 end end end;
if not bX.t then if C.fly and C.parado then local N=m()local a2,a0=Z(N),X(N)if a2 and a0 and a0.Health>0 then if not bX.s or bX.s.hum~=a0 then bX.s={hum=a0,autoRotate=a0.AutoRotate,platformStand=a0.PlatformStand}
end;
a0.PlatformStand=true;
if not bX.h then bX.h=a2.CFrame end;
a2.AssemblyLinearVelocity=k(0,0,0)a2.AssemblyAngularVelocity=k(0,0,0)a2.CFrame=bX.h end else bX.h=nil end;
return end;
bX.h=nil;
local bT=m()local bo,cd=Z(bT),X(bT)if not bo or not cd or cd.Health<=0 then return end;
if not bX.s or bX.s.hum~=cd then bX.s={hum=cd,autoRotate=cd.AutoRotate,platformStand=cd.PlatformStand}end;
cd.AutoRotate=false;
cd.PlatformStand=C.fly;
local ce=Z(bX.t)local cf=ce.Position;
local cg=bo.Position;
local ch=cf;
bX.sp=0;
if C.ant then bX.tm=(bX.tm or 0)+bJ;
local ci=bX.tm;
if bX.l~=bX.t then bX.l=bX.t;
bX.hs={}bX.ld=k(0,0,0)end;
local cj=bX.hs;
if cj[1]and(cf-cj[#cj].p).Magnitude>40 then cj={}bX.hs=cj;
bX.ld=k(0,0,0)end;
cj[#cj+1]={t=ci,p=cf}while cj[1]and ci-cj[1].t>0.3 do table.remove(cj,1)end;
local ck=k(0,0,0)local cl=ci-cj[1].t;
if#cj>2 and cl>=0.1 then local I=(cf-cj[1].p)/cl;
I=k(I.X,0,I.Z)if I.Magnitude>250 then I=I.Unit*250 end;
bX.sp=I.Magnitude;
local a7,cm=pcall(h.GetNetworkPing,h)cm=a7 and type(cm)=="number"and cm>0 and cm*2 or 0.1;
ck=I*math.min(cm*C.antecipa,1)if ck.Magnitude>C.antlim then ck=ck.Unit*C.antlim end end;
bX.ld=bX.ld+(ck-bX.ld)*math.min(1,bJ*8)ch=cf+bX.ld else bX.l=nil end;
if C.fly then bo.AssemblyLinearVelocity=k(0,0,0)bo.AssemblyAngularVelocity=k(0,0,0)local cn=ce.CFrame.LookVector;
local co=k(cn.X,0,cn.Z)if co.Magnitude<0.01 then co=k(0,0,-1)else co=co.Unit end;
local cp=ch-co*bW+k(0,C.altura,0)local b_=cp-bo.Position;
local cq=b_.Magnitude;
local cr=math.max(C.velFly,math.min(bX.sp*1.5,400))*bJ;
if cr~=cr then cr=0 end;
if cq<0.05 or cq<=cr then cg=cp else cg=bo.Position+b_.Unit*cr end end;
local cs=k(cf.X,cg.Y,cf.Z)if(cs-cg).Magnitude>0.05 then bo.CFrame=bY(cg,cs)else bo.CFrame=CFrame.new(cg)*(bo.CFrame-bo.CFrame.Position)
end;
local ct=e.CurrentCamera;
if ct then local cu=ct.CFrame.Position;
if(cf-cu).Magnitude>0.05 then local cv=bY(cu,cf)local cw=ct.ViewportSize.Y;
if cw>0 then local cx=math.atan(E/(cw/2)*math.tan(math.rad(ct.FieldOfView)/2))cv=cv*CFrame.Angles(-cx,0,0)end;
ct.CFrame=cv end end end;
local function cy(bJ)if not y.running then return end;
local V,W=pcall(cb,bJ)if not V then warn("[HubBlox] "..tostring(W))end end;
if not pcall(function()b:BindToRenderStep("HubBloxAim",Enum.RenderPriority.Camera.Value+1,cy)end)then K(b.RenderStepped,cy)
end;
K(b.Stepped,function()if C.fly then pcall(c8,true)end end)end)

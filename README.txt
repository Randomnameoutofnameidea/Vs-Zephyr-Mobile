For command terminal

class Item:
    def __init__(self, name, type, num, info):
        self.name = name
        self.type = type
        self.num = num
        self.info = info
        itemDict[name] = self

class Player:
    def __init__(self, name, classes, tempClass, base, setNum=None, newNum=None, addBase=None, hp=20, maxhp=20, attack=20, defense=20, speed=20, mana=50, maxMana=100, damage=1, range=1, productivity=0, spare=0, weapon=noWeapon, armour=noArmour, level=1, xp=0, fight=[], inventory=None, action=[], skills=[], status='Neutral', info='Checked', buff=None, passiveBuff=None, color=(255, 255, 255), skinList=['Default'], skin='Default'):

        if buff is None:
            buff = {}
        if passiveBuff is None:
            passiveBuff = {}
        if addBase is None:
            addBase = {'attack':{}, 'defense':{}, 'speed':{}, 'hp':{}, 'range':{}, 'maxhp':{}, 'productivity':{}, 'damage':{}}
        if setNum is None:
            setNum = []
        if newNum is None:
            newNum = copy.copy(setNum)
        if inventory is None:
            inventory = placeHolder_inventory
        self.setNum = setNum
        self.newNum = newNum
        self.name = name
        self.classes = classes
        self.tempClass = tempClass
        self.base = base
        self.addBase = addBase
        self.attack = attack
        self.defense = defense
        self.speed = speed
        self.range = range
        self.productivity = productivity
        self.mana = mana
        self.maxMana = maxMana
        self.damage = damage
        self.spare = spare
        self.weapon = weapon
        self.armour = armour
        self.level = level
        self.xp = xp
        self.fight = fight
        self.inventory = inventory
        self.action = action
        self.skills = skills
        self.hp = hp
        self.maxhp = maxhp
        self.status = status
        self.color = color
        self.info = info
        self.buff = buff
        self.passiveBuff = passiveBuff
        self.skin = skin
        self.skinList = skinList

class Skill:
    #def __init__(self, name, cost, type, info, baseNum, num, turn, multiNum, target, effects):
    def __init__(self, name, cost=10, info='Skill', type='ally:', baseNum=10, num=10, numCap=30, usePercent=False, cooldown='0T', targetType='Single', repeatHowMany=1, targetAmount=1, useAnim=False, animType='Thrower', stackDuration=False, stackAmplifier=False, applyEffect=None, removeEffect=None):
        if applyEffect == None:
            applyEffect = {}
        if removeEffect == None:
            removeEffect = {}
        self.name = name
        self.cost = cost
        self.info = info
        self.type = type
        self.baseNum = baseNum
        self.num = num
        self.numCap = numCap
        self.usePercent = usePercent
        self.cooldown = cooldown
        self.targetType = targetType #Self, Single, Multiple, All
        self.repeatHowMany = repeatHowMany
        self.targetAmount = targetAmount
        #Effects Below
        self.useAnim = useAnim
        self.animType = animType
        self.stackDuration = stackDuration
        self.stackAmplifier = stackAmplifier
        self.applyEffect = applyEffect
        self.removeEffect = removeEffect
        skillDict[name] = self

class Effect:
    def __init__(self, name, type, info, num, usePercent=False, multiplier=1, stackable=False, applyRepeated=False, delay='0T', doStun=False, useVisual=False, affectWhat=None, color=(255, 255, 255)):
        if affectWhat == None:
            affectWhat = {'hp': 30}
        self.name = name
        self.type = type
        self.num = num
        self.doStun = doStun
        self.info = info
        self.multiplier = multiplier
        self.stackable = stackable
        self.applyRepeated = applyRepeated
        self.delay = delay
        self.useVisual = useVisual
        self.color = color
        effectList.append(self)

class Act:
    def __init__(self, name, desc, sparingPoints, energyPoints, checkAttack, useOn):#, usePattern, number):

      self.name = name

      self.desc = desc

      self.sparingPoints = sparingPoints

      self.energyPoints = energyPoints

      self.checkAttack = checkAttack

      self.useOn = useOn

class Fight:
    def __init__(self, name, infoClass, classType, info, range='Default', baseAttack='Default', attack='Default', bars=None, useHitChance=False, hitChanceEquation='95-Range*10', stackDuration=False, stackAmplifier=False, applyEffect=None, removeEffect=None):
        if applyEffect == None:
            applyEffect = {}
        if removeEffect == None:
            removeEffect = {}
        if bars == None:
            bars = ['A1']
        fightDict[name] = self
        #classType = 'Back' if classType in ['Melee', 'Tank'] else 'Support'
        self.name = name
        self.infoClass = infoClass
        self.classType = classType
        self.info = info
        self.bars = bars
        self.range = range
        self.useHitChance = useHitChance
        self.stackDuration = stackDuration
        self.hitChanceEquation = hitChanceEquation
        self.stackAmplifier = stackAmplifier
        self.applyEffect = applyEffect
        self.removeEffect = removeEffect
        self.baseAttack = baseAttack
        self.attack = attack
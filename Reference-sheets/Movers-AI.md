# Movers AI Interface


| AII id | Class | Example of monsters | Comment |
| ----- | ----- | -------------------- | ------- |
| AII_MOVER | *None* | MI_MALE, MI_FEMALE, MI_DEFAULT | *For players* | 
| AII_MONSTER | `CAIMonster` | MI_AIBATT1, MI_AIBATT4, ..., MI_GUARDIAN, MI_RANGDA, MI_VEMPAIN, MI_DESIBIGFOOT | |
| AII_VER2_TYPE0 | `CAIMonster2` | *None* |  |
| AII_CLOCKWORKS | `CAIClockWorks` | MI_CLOCKWORKS and his friends | |
| AII_EGG | `CAIEgg` | MI_PET_WHITETIGER01, ... | [1] |
| AII_PET | `CAIPet` | MI_PET_YETI, ... | |
| AII_NONE | *None* | MI_MAFL_LOSHA, MI_NPC_RAINBOWSTART, ... | |
| AII_BIGMUSCLE | `CAIBigMuscle` | MI_BIGMUSCLE	 | |
| AII_KRRR | `CAIKrrr` | MI_KRRR	 | |
| AII_BEAR | `CAIBear` | MI_MUSHMOOT	 | |
| AII_METEONYKER | `CAIMeteonyker` | Red Meteonyker | |
| AII_AGGRO_NORMAL (v16) | ? | MI_STATUE, MI_SPIRITTULA, MI_SPIRITUMTULA, MI_BEHEMOTH, MI_BEHESTATUE01, MI_BASILISK, All in Kalgas | |
| AII_PARTY_AGGRO_LEADER (v17) | ? | MI_RUGALKUMA, MI_RUGALRIMA | |
| AII_PARTY_AGGRO_SUB (v17) | ? | MI_RUGALHEAT02, MI_RUGALWIND02 | |
| AII_ARENA_REAPER (v17) | ? | MI_EVENT_FWCMONSTER | |
| AII_BEETLE (v22) | *Unreleased* | MI_BEETLE2 | [2] |


*Notes:*

- [1] This kind of pets as movers do not exist in WorldServer. The client creates a "fake" mover if a mover has an "activated system pet".
- [2] Because v22 source code never leaked, and because there are almost no footage
of the Floating Castle dungeon on Youtube, the behavior related to `AII_BEETLE` is
mostly unknown.

# ZA Triage Training

For development of the Zulu-Alpha Triage training script, called `multi_manikin.sqf`

## Documentation from `multi_manikin.sqf`

    Author: Phoenix

    Description: For creating a mass casualty incident with multiple casualties and
    		     providing options to manage them.

    Params:
      0: OBJECT - The controller object that the other objects are synced to.

    Usage: Place down a game logic, and in it's init initialize this script.
           Then synchronize one or more shooting mats to spawn the manikins on top of.
    	   Then synchronize one or more cones to add the addaction options to start or
           stop the script.
           Then, add the variable `multi_manikin_casualty' to the name spaces
    	   of each of the synchronized mats, where the contents of those variables follows
    	   the format:
    		0: ARRAY - Any number of nested arrays specifying the wounds, of format:
    			0: NUMBER - Damage of wound
    			1: STRING - Body part
    			2: STRING - Wound type

    	So for example, in the init of the control object, put:
    		`nul = [this] execVM "multi_manikin.sqf";`

    	Then synchronize it to several mats, and in each of those mats, put in their init:
    		this setVariable [
    			"multi_manikin_casualty",
    			[
    				[0.5, "LeftArm", "bullet"],
    				[0.3, "Body", "shell"]
    			],
    			true
    		];

    	Then synchronize the game logic to a cone. Nothing needs to be in the init of that
        cone.

    	Valid mat objects are: ShootingMat_01_Olive_F, ShootingMat_01_Khaki_F,
    	                       ShootingMat_01_OPFOR_F
    	Valid cone objects are: RoadCone_L_F, Land_RoadCone_01_F, RoadCone_F

    Reference:
    	Body parts: Head, Body, LeftArm, RightArm, LeftLeg, RightLeg

    	damageTypes: bullet, grenade, explosive, shell, vehiclecrash, collision,
    	backblast, stab, punch, falling, ropeburn, drowning, unknown

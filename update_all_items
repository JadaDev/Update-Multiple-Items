DELIMITER $$

CREATE PROCEDURE UpdateStatValues()
BEGIN
    DECLARE statType INT;
    DECLARE done INT DEFAULT 0;
    
    -- loop through all stat types that need updates, edited it the way you want.
    DECLARE statTypesCursor CURSOR FOR 
        SELECT DISTINCT stat_type 
        FROM (
            SELECT 3 AS stat_type -- Agility
            UNION SELECT 4         -- Strength
            UNION SELECT 5         -- Intellect
            UNION SELECT 6         -- Spirit
            UNION SELECT 7         -- Stamina
            UNION SELECT 38        -- Attack Power
            UNION SELECT 39        -- Ranged Attack Power
            UNION SELECT 40        -- Feral Attack Power
            UNION SELECT 41        -- Spell Healing Done
            UNION SELECT 42        -- Spell Damage Done
            UNION SELECT 45        -- Spell Power
        ) AS statTypes;

    DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = 1;

    OPEN statTypesCursor;

    statLoop: LOOP
        FETCH statTypesCursor INTO statType;
        IF done THEN 
            LEAVE statLoop; 
        END IF;

        SET @query = CONCAT(
            'UPDATE item_template SET ',
            'stat_value1 = stat_value1 / 10 WHERE stat_type1 = ', statType, '; ',
            'UPDATE item_template SET ',
            'stat_value2 = stat_value2 / 10 WHERE stat_type2 = ', statType, '; ',
            'UPDATE item_template SET ',
            'stat_value3 = stat_value3 / 10 WHERE stat_type3 = ', statType, '; ',
            'UPDATE item_template SET ',
            'stat_value4 = stat_value4 / 10 WHERE stat_type4 = ', statType, '; ',
            'UPDATE item_template SET ',
            'stat_value5 = stat_value5 / 10 WHERE stat_type5 = ', statType, '; ',
            'UPDATE item_template SET ',
            'stat_value6 = stat_value6 / 10 WHERE stat_type6 = ', statType, '; ',
            'UPDATE item_template SET ',
            'stat_value7 = stat_value7 / 10 WHERE stat_type7 = ', statType, '; ',
            'UPDATE item_template SET ',
            'stat_value8 = stat_value8 / 10 WHERE stat_type8 = ', statType, '; ',
            'UPDATE item_template SET ',
            'stat_value9 = stat_value9 / 10 WHERE stat_type9 = ', statType, '; ',
            'UPDATE item_template SET ',
            'stat_value10 = stat_value10 / 10 WHERE stat_type10 = ', statType, ';'
        );

        PREPARE stmt FROM @query;
        EXECUTE stmt;
        DEALLOCATE PREPARE stmt;
    END LOOP;

    CLOSE statTypesCursor;
END$$

DELIMITER ;

CALL UpdateStatValues();

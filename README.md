-- Function: matchd(text)

-- DROP FUNCTION matchd(text);

CREATE OR REPLACE FUNCTION matchd(s text)
  RETURNS text AS
$BODY$DECLARE
	ltr text;
	nm1 text;
	nm2 text;
	nm text;
	pos integer;
	len integer;
	--t integer;
BEGIN
	len := length(s);
	pos := 1;
	<<ablock>>
	BEGIN
	LOOP
		ltr := substring(s from pos for 3);
		IF substring(ltr from 1 for 1) != ' ' AND substring(ltr from 2 for 1) != ' ' AND substring(ltr from 3 for 1) != ' ' AND substring(ltr from 1 for 1) != '.' AND substring(ltr from 2 for 1) != '.' AND substring(ltr from 3 for 1) != '.' THEN
			pos := pos-1;
			EXIT ablock;
			pos := pos+1;
		END IF;
		pos :=pos + 1;
	EXIT WHEN pos > len;
	END LOOP;
	END;
	nm1 := substring(s from (pos+1));
	nm2 := (substring(nm1 from 1 for position(' ' in concat(nm1, ' '))-1));
	nm := (substring(nm2 from 1 for position('.' in concat(nm2, '.'))-1));
	return dmetaphone_alt(nm);
	
END;$BODY$
  LANGUAGE plpgsql VOLATILE
  COST 100;
ALTER FUNCTION matchd(text)
  OWNER TO postgres;


------------------------------------------------------------

-- Function: matchm(text)

-- DROP FUNCTION matchm(text);

CREATE OR REPLACE FUNCTION matchm(s text)
  RETURNS text AS
$BODY$DECLARE
	ltr text;
	nm1 text;
	nm2 text;
	nm text;
	pos integer;
	len integer;
	--t integer;
BEGIN
	len := length(s);
	pos := 1;
	<<ablock>>
	BEGIN
	LOOP
		ltr := substring(s from pos for 3);
		IF substring(ltr from 1 for 1) != ' ' AND substring(ltr from 2 for 1) != ' ' AND substring(ltr from 3 for 1) != ' ' AND substring(ltr from 1 for 1) != '.' AND substring(ltr from 2 for 1) != '.' AND substring(ltr from 3 for 1) != '.' THEN
			pos := pos-1;
			EXIT ablock;
			pos := pos+1;
		END IF;
		pos :=pos + 1;
	EXIT WHEN pos > len;
	END LOOP;
	END;
	nm1 := substring(s from (pos+1));
	nm2 := (substring(nm1 from 1 for position(' ' in concat(nm1, ' '))-1));
	nm := (substring(nm2 from 1 for position('.' in concat(nm2, '.'))-1));
	return dmetaphone_alt(nm);
	
END;$BODY$
  LANGUAGE plpgsql VOLATILE
  COST 100;
ALTER FUNCTION matchm(text)
  OWNER TO postgres;

------------------------------------------------------------------------


-- Function: matchs(text)

-- DROP FUNCTION matchs(text);

CREATE OR REPLACE FUNCTION matchs(s text)
  RETURNS text AS
$BODY$DECLARE
	ltr text;
	nm1 text;
	nm2 text;
	nm text;
	pos integer;
	len integer;
	--t integer;
BEGIN
	len := length(s);
	pos := 1;
	<<ablock>>
	BEGIN
	LOOP
		ltr := substring(s from pos for 3);
		IF substring(ltr from 1 for 1) != ' ' AND substring(ltr from 2 for 1) != ' ' AND substring(ltr from 3 for 1) != ' ' AND substring(ltr from 1 for 1) != '.' AND substring(ltr from 2 for 1) != '.' AND substring(ltr from 3 for 1) != '.' THEN
			pos := pos-1;
			EXIT ablock;
			pos := pos+1;
		END IF;
		pos :=pos + 1;
	EXIT WHEN pos > len;
	END LOOP;
	END;
	nm1 := substring(s from (pos+1));
	nm2 := (substring(nm1 from 1 for position(' ' in concat(nm1, ' '))-1));
	nm := (substring(nm2 from 1 for position('.' in concat(nm2, '.'))-1));
	return soundex(nm);
	
END;$BODY$
  LANGUAGE plpgsql VOLATILE
  COST 100;
ALTER FUNCTION matchs(text)
  OWNER TO postgres;

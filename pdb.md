# chimera

## distance between residues

distance :78.a@ca :89.a@ca
rlabel :25.a@ca

## viz
open XX.pdb
~ribbon;
~disp :.A,:.B
delete solvent; 
delete :SPD; 
disp ligand; select ligand;color green ligand
surface probeRadius 1.4;
light mode single
rangecol bfactor -8 blue 0 white 8 red
turn z -10; turn y 210; turn x 5; 

~ribbon; ~disp :.A,:.B; delete solvent; delete :SPD; disp ligand; select ligand;color green ligand; surface probeRadius 1.4; light mode single; rangecol bfactor -6 blue 0 white 6 red; turn z 115; turn y 210; turn x 5; focus :;

copy file filename_chimera.png png

select :.A
surftrans 50

#jmol: eg. 1BO4
select all; wireframe off;spacefill off; backbone off; isosurface off;cartoon off;background [200 200 200];
select [COA]; wireframe on; color black;
select [COA]300:A.N4P;spacefill 200; 
select [COA]300:B.N4P;spacefill 200;
select protein;center selected;
isosurface saSurface molecular map property temperature colorScheme bwr;
isosurface solvent 0 molecular map property temperature colorScheme bwr;

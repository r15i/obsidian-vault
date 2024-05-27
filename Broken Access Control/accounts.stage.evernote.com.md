trying to levarege the fact the 
f3be06e93f6c7f1fb53e60b69c59c8df8e084d5bd3efad83708602f5451a17d2.jHdpNyMVD%2BBolB2lkycupwXZSpub2sBNd18EiuLHdAU

is always divided into 2 partes


also i'm trying to get 

https://accounts.evernote.com/test/login/%XX%XX 
TO output some XSS FROM THE URL 
there are weird behavuoirs with 
- ../ 
- %00 the null terminator return a completely different 404 page 

also i tried to bruteforce the behaviour of the url encoding by by tring all the %XX paramenter now i should try with the %XX%XX%XX as specifiend in the utf encoding 
**noting that the dollar sign **

|€|%80|%E2%82%A|
are treated differently if encoded in |From Windows-1252|From UTF-|














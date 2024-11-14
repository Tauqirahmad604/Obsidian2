
1. Install pm2

```
   sudo npm install pm2 -g
```

2. Check version for pm2

```
   pm2 --version
```

3. Check status of pm2

```
   pm2 status
```
   ![[Pasted image 20240627171322.png]]

 4. To start service you want

```
pm2 start npm --name "devLanding" -- run start
```

5. Then check status of service

```
  pm2 status
```

6. To save pm2

```
  pm2 save
```


1y]$L[6iO)|{_m%1
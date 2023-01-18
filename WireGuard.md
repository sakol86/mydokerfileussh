                                                          Установка VPN Wiregurad с интерфейсом​

docker run -d \
  --name=wg-easy \
  -e WG_HOST=YOUR_SERVER_IP \
  -e PASSWORD=YOUR_ADMIN_PASSWORD \
  -v ~/.wg-easy:/etc/wireguard \
  -p 51820:51820/udp \
  -p 51821:51821/tcp \
  --cap-add=NET_ADMIN \
  --cap-add=SYS_MODULE \
  --sysctl="net.ipv4.conf.all.src_valid_mark=1" \
  --sysctl="net.ipv4.ip_forward=1" \
  --restart unless-stopped \
  weejewel/wg-easy


                                                          Должно получиться так:
                                                          
![image](https://user-images.githubusercontent.com/86907205/213125523-2a75e572-a439-40ad-8936-e0f06330a6d0.png)


Вместо "YOUR_SERVER_IP" пишем ваш IP-адрес сервера.
Вместо "YOUR_ADMIN_PASSWORD" пишем пароль, который вы хотите использовать для входа в веб-интерфейс своего VPN.




Для входа в веб-интерфейс используем 0.0.0.0:51821, где 0.0.0.0 IP-адрес вашего сервера. В моем случае, это 79.137.197.187:51821. При переходе, у вас открывается форма ввода пароля, заполняем и входим в веб-интерфейс нашего VPN.

![image](https://user-images.githubusercontent.com/86907205/213126431-a4acbf7d-3e6e-44f1-ae29-29daaa074857.png)



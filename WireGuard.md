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

Вместо "YOUR_SERVER_IP" пишем ваш IP-адрес сервера.
Вместо "YOUR_ADMIN_PASSWORD" пишем пароль, который вы хотите использовать для входа в веб-интерфейс своего VPN.
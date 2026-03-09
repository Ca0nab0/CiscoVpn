# CiscoVpn



Objetivos

- IPsec IKEv1/IKEv2 (Políticas): Proteger el tráfico LAN-to-LAN mediante túneles seguros. IKEv2 se utiliza para modernizar la seguridad con algoritmos AES-256 y SHA-256.

- IPsec VTI (Virtual Tunnel Interface): Simplificar el diseño de la red permitiendo el enrutamiento directo de paquetes hacia una interfaz de túnel, evitando el uso de ACLs complejas de "tráfico interesante".

- Túnel GRE sobre IPsec: Habilitar el transporte de tráfico Multicast necesario para los protocolos de enrutamiento dinámico.

- DMVPN (Fase 2/3): Implementar una solución escalable donde los Spokes puedan comunicarse entre sí dinámicamente sin saturar al Hub, utilizando NHRP para la resolución de direcciones.

Capturas de pantalla de puntos clave


Creacion de propuesta


<img width="1077" height="131" alt="image" src="https://github.com/user-attachments/assets/de4acbdc-9f99-42a6-ac3e-f921f9d134cc" />

Politica de negociacion


<img width="828" height="422" alt="image" src="https://github.com/user-attachments/assets/2623a0e6-e757-4e10-bb5a-6c0de1a858e7" />

IPSec y Tunel VPN

<img width="712" height="281" alt="image" src="https://github.com/user-attachments/assets/723bbadf-ef58-4b2f-aadd-573ae2af3ec8" />

- Enrutamiento

DMVPNv1

  
<img width="621" height="163" alt="image" src="https://github.com/user-attachments/assets/e08a45a3-f6ec-45da-8a16-410dc76c1341" />


DMVPNv2

  
<img width="655" height="99" alt="image" src="https://github.com/user-attachments/assets/f416a687-7f1d-4082-8b16-7d0ac4bcc51a" />

Topologia

<table border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; width: 100%; font-family: Arial, sans-serif;">
  <thead style="background-color: #4CAF50; color: white;">
    <tr>
      <th>Dispositivo</th>
      <th>Interfaz</th>
      <th>Dirección IP</th>
      <th>Descripción</th>
    </tr>
  </thead>
  <tbody>
    <tr style="background-color: #f2f2f2;">
      <td><strong>ISP</strong></td>
      <td>G1/0</td>
      <td>1.1.1.2/30</td>
      <td>Core del Proveedor</td>
    </tr>
    <tr>
      <td><strong>ISP</strong></td>
      <td>G2/0</td>
      <td>2.2.2.2/30</td>
      <td>Core del Proveedor</td>
    </tr>
    <tr style="background-color: #f2f2f2;">
      <td><strong>ISP</strong></td>
      <td>G3/0</td>
      <td>3.3.3.2/30</td>
      <td>Core del Proveedor</td>
    </tr>
    <tr>
      <td><strong>Peer1 / Hub</strong></td>
      <td>G1/0 (WAN)</td>
      <td>1.1.1.1/30</td>
      <td>Sede Principal / Terminación VPN</td>
    </tr>
    <tr style="background-color: #f2f2f2;">
      <td><strong>Peer2 / Spoke1</strong></td>
      <td>G1/0 (WAN)</td>
      <td>2.2.2.1/30</td>
      <td>Sede Remota A</td>
    </tr>
    <tr>
      <td><strong>Outsider / Spoke2</strong></td>
      <td>G1/0 (WAN)</td>
      <td>3.3.3.1/30</td>
      <td>Sede Remota B / Usuario Externo</td>
    </tr>
    <tr style="background-color: #f2f2f2;">
      <td><strong>LAN Sede 1</strong></td>
      <td>F0/0</td>
      <td>10.3.75.1/24</td>
      <td>Red Interna (DHCP Pool: vpnr2)</td>
    </tr>
    <tr>
      <td><strong>LAN Sede 2</strong></td>
      <td>F0/0</td>
      <td>10.3.76.1/24</td>
      <td>Red Interna (DHCP Pool: vpnr3)</td>
    </tr>
  </tbody>
</table>


Parametros usados


<table border="1" cellpadding="10" cellspacing="0" style="border-collapse: collapse; width: 100%; font-family: Arial, sans-serif;">
  <thead style="background-color: #2c3e50; color: white;">
    <tr>
      <th style="width: 25%;">Parámetro</th>
      <th style="width: 37.5%; background-color: #3498db;">Configuración IKEv1</th>
      <th style="width: 37.5%; background-color: #27ae60;">Configuración IKEv2</th>
    </tr>
  </thead>
  <tbody>
    <tr style="background-color: #f9f9f9;">
      <td><strong>Algoritmo de Cifrado</strong></td>
      <td>AES-CBC-128 / 256</td>
      <td>AES-CBC-256</td>
    </tr>
    <tr>
      <td><strong>Hash de Integridad</strong></td>
      <td>SHA-1</td>
      <td>SHA-256</td>
    </tr>
    <tr style="background-color: #f9f9f9;">
      <td><strong>Método Diffie-Hellman</strong></td>
      <td>Group 2 / 14</td>
      <td>Group 14 (2048-bit)</td>
    </tr>
    <tr>
      <td><strong>Autenticación</strong></td>
      <td>PSK (Pre-Shared Key)</td>
      <td>PSK (Local/Remote Keyring)</td>
    </tr>
  </tbody>
</table>

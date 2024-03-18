import socket

ip_address = '192.168.2.240'
port = 41300

# Datos para controlar la electroválvula (debes ajustar estos valores según la especificación de tu dispositivo)
command = b'\x01\x01\x00\x04\x00\x00\x00\x00\x00\x00\x00\x00\x02\x00\x01\x00'
valve_state = True


if valve_state:
    command = command[:11] + b'\x01' + command[12:]
else:
    command = command[:11] + b'\x00' + command[12:]


with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:

    s.connect((ip_address, port))
    s.sendall(command)
    response = s.recv(1024)

    print("Respuesta del dispositivo:", response)

# CHAT-BOT-CAFETERI-A-UNIFRANZ-
ESTO ES NUESTRO CHAT BOT DE CAFETERÍA UNIFRANZ PARA ATENCIÓN AL CLIENTE ESPERO QUE LE GUSTE 
from flask import Flask, request, jsonify
from twilio.twiml.messaging_response import MessagingResponse

app = Flask(__name__)

@app.route('/webhook', methods=['POST'])
def whatsapp_bot():
    incoming_msg = request.values.get('Body', '').strip().lower()
    response = MessagingResponse()
    message = response.message()

    if 'hola' in incoming_msg:
        message.body("¡Hola! Bienvenido/a a la cafetería en línea de Unifranz. ¿En qué puedo ayudarte hoy?")
    
    elif 'chau' in incoming_msg or 'gracias' in incoming_msg:
        message.body("Gracias por contactarte con Cafetería Unifranz. ¡Que tengas un excelente día!")
    
    elif 'menú' in incoming_msg:
        message.body("(Respuesta de menú)")
    
    elif 'horarios' in incoming_msg:
        message.body("Atendemos desde las 7:00 de la mañana a 10 de la noche.")

    elif 'descuento' in incoming_msg or 'estudiantes' in incoming_msg:
        message.body("Sí, los estudiantes de Unifranz tienen un 10% de descuento en la mayoría de los productos al presentar su carnet de estudiante.")

    elif 'productos sin azúcar' in incoming_msg or 'sin calorías' in incoming_msg:
        message.body("Sí, contamos con productos sin azúcar como postres light y opciones bajas en calorías como ensaladas y wraps saludables.")

    elif 'bebidas sin cafeína' in incoming_msg:
        message.body("Sí, ofrecemos varias opciones de bebidas sin cafeína, como tés de hierbas, jugos naturales, smoothies y nuestra propia bebida Aguafranz.")

    elif 'cuánto tiempo demora' in incoming_msg:
        message.body("El tiempo promedio de espera para un pedido es entre 5 y 20 minutos, dependiendo de la cantidad de clientes.")

    elif 'métodos de pago' in incoming_msg:
        message.body("Aceptamos pagos en efectivo, tarjetas de débito y crédito, así como pagos mediante transferencias bancarias y aplicaciones móviles como QR Simple y Tigo Money.")

    elif 'servicio a domicilio' in incoming_msg:
        message.body("Actualmente no ofrecemos servicio a domicilio, pero puedes hacer pedidos en línea y recogerlos en la cafetería.")

    elif 'contactar servicio al cliente' in incoming_msg:
        message.body("Si tienes algún inconveniente, puedes contactarnos respondiendo a este chat o llamando al +591 76711991.")

    else:
        message.body("Lo siento, no entiendo tu pregunta. ¿Podrías intentar con algo diferente o hablar con un agente humano?")

    return str(response)

if __name__ == '__main__':
    app.run(debug=True)

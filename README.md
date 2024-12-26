from flask import Flask, request # type: ignore

app = Flask(__name__)

@app.route('/')
def home():
    return '''
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>THE PARADISE - Resort & Spa Hotel</title>
        <style>
            body {
                background-image: url('/static/images/background.jpg');
                background-size: cover;
                background-repeat: no-repeat;
                background-attachment: fixed;
                color: #fff;
                font-family: Arial, sans-serif;
            }
            header, footer {
                background-color: rgba(0, 0, 0, 0.7);
                text-align: center;
                padding: 20px;
            }
            header h1, header p {
                margin: 0;
            }
            main {
                background-color: rgba(0, 0, 0, 0.6);
                padding: 20px;
                border-radius: 10px;
                margin: 20px;
            }
            h2 {
                text-align: center;
            }
            .room {
                display: inline-block;
                margin: 10px;
                text-align: center;
            }
            img {
                border-radius: 10px;
                width: 300px;
                height: auto;
            }
        </style>
    </head>
    <body>
        <header>
            <h1>THE PARADISE</h1>
            <p>Resort & Spa Hotel</p>
        </header>

        <main>
            <section id="rooms">
                <h2>Our Rooms</h2>
                <div class="room" id="deluxe-room">
                    <img src="C:\Users\Het\Desktop\website design 2\d41e5764-7393-4f34-b37b-6424c0d6f9ea.jpg" alt="Deluxe Room">
                    <h3>Deluxe Room</h3>
                    <p>Price: $120/night</p>
                </div>
                <div class="room" id="suite-room">
                    <img src="C:\Users\Het\Downloads\e0b0801a-541d-4aa5-9402-08a6fa81add0.jpg" alt="Suite Room">
                    <h3>Suite Room</h3>
                    <p>Price: $200/night</p>
                </div>
                <div class="room" id="family-room">
                    <img src="C:\Users\Het\Downloads\a0bf9e7a-5480-419e-a6f0-fca7c7e42003.jpg" alt="Family Room">
                    <h3>Family Room</h3>
                    <p>Price: $180/night</p>
                </div>
            </section>

            <section id="booking">
                <h2>Book Your Stay</h2>
                <form action="/book" method="post">
                    <label for="name">Full Name:</label>
                    <input type="text" id="name" name="name" required><br>

                    <label for="email">Email:</label>
                    <input type="email" id="email" name="email" required><br>

                    <label for="mobile">Mobile No:</label>
                    <input type="tel" id="mobile" name="mobile" required><br>

                    <label for="checkin">Check-in Date:</label>
                    <input type="date" id="checkin" name="checkin" required><br>

                    <label for="checkout">Check-out Date:</label>
                    <input type="date" id="checkout" name="checkout" required><br>

                    <label for="room">Select Room:</label>
                    <select id="room" name="room">
                        <option value="deluxe">Deluxe Room</option>
                        <option value="suite">Suite Room</option>
                        <option value="family">Family Room</option>
                    </select><br>

                    <label for="payment">Payment Method:</label>
                    <select id="payment" name="payment">
                        <option value="debit">Debit Card</option>
                        <option value="upi">UPI</option>
                        <option value="other">Other</option>
                    </select><br>

                    <button type="submit">Confirm Booking</button>
                </form>
            </section>

            <section id="facilities">
                <h2>Facilities</h2>
                <ul>
                    <li>Swimming Pool</li>
                    <li>Spa and Wellness Center</li>
                    <li>Free Wi-Fi</li>
                    <li>Gym</li>
                    <li>24/7 Room Service</li>
                </ul>
            </section>

            <section id="nearby-places">
                <h2>Nearby Places to Visit</h2>
                <ul>
                    <li>City Museum - 2 km</li>
                    <li>Paradise Beach - 5 km</li>
                    <li>Hilltop Park - 10 km</li>
                    <li>Shopping Mall - 3 km</li>
                </ul>
            </section>
        </main>

        <footer>
            <p>&copy; 2024 THE PARADISE. All Rights Reserved.</p>
        </footer>
    </body>
    </html>
    '''

@app.route('/book', methods=['POST'])
def book():
    name = request.form['name']
    email = request.form['email']
    mobile = request.form['mobile']
    checkin = request.form['checkin']
    checkout = request.form['checkout']
    room = request.form['room']
    payment = request.form['payment']

    return f"Thank you for booking, {name}. Your check-in date is {checkin} and check-out date is {checkout}. Room type: {room}. Payment method: {payment}."

if __name__ == '__main__':
    app.run(debug=True)

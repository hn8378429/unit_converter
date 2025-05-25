import streamlit as st

#custom
st.markdown(
    """
    <style>
    body {
    background-color:rgb(7, 7, 24)
    color: white;
    }
    .stApp{
        background: linear-gradient(135deg,rgb(226, 218, 218),rgb(12, 51, 85));
        padding: 30px;
        border-radius: 15px;
        box-shadow: 0px 10px 30px rgba(0, 0, 0, 0.3);
    }
    h1 {
        text-align: center;
        font-size: 40px;
        color:white;
    }
    .stButton>button {  
        background: linear-gradient(45deg, #0b5394, #351c75);
        color: white;
        font-size: 11px;
        padding: 10px 20px;
        border-radius: 11px;
        transition: background 0.3s ease;
        box-shadow: 0px 5px 15px rgba(0, 201, 255, 0.4);
    }
    .stButton>button:hover {
        transform: scale(1.05);
        background: linear-gradient(45deg,rgb(156, 198, 233), #00c9ff);
        color: black;
    }
    .result-box {
        font-size: 20px;
        font-weight: bold;
        text-align: center;
        background-color: grey;
        padding: 25px;
        border-radius: 10px;
        color:rgb(26, 13, 100);
        margin-top: 20px;
        box-shadow: 0px 5px 15px rgba(3, 6, 7, 0.4);
    }
    .footer {
        text-align: center;
        font-size: 20px;
        color: black;
        margin-top: 50px;
    }

    </style>
    """, 
    unsafe_allow_html=True
)

#title and description
st.markdown("<h1>Unit Convertor</h1>", unsafe_allow_html=True)
st.write("Easily convert units from one to another with our unit convertor.")

#sidebar
conversion_type = st.sidebar.selectbox("Select Conversion Type", ["Length", "Weight", "Temperature"])

#Input value
value = st.number_input("Enter the value to convert", value=0.0, min_value=0.0, step=0.1)

#layout for unit selection
col1, col2 = st.columns(2)


#conversion logic
if conversion_type == "Length":
    with col1:
        from_unit = st.selectbox("From", ["Meters", "Feet", "Miles", "Kilometers", "Inches", "yards", "centimeters"])
    with col2:
        to_unit = st.selectbox("To", ["Meters", "Feet", "Miles", "Kilometers", "Inches", "yards", "centimeters"])
elif conversion_type == "Weight":
    with col1:
        from_unit = st.selectbox("From", ["Kilograms", "Pounds", "Grams", "Ounces", "Milligrams", "Stones"])
    with col2:
        to_unit = st.selectbox("To", ["Kilograms", "Pounds", "Grams", "Ounces", "Milligrams", "Stones"])
elif conversion_type == "Temperature":
    with col1:  
        from_unit = st.selectbox("From", ["Celsius", "Fahrenheit", "Kelvin"])
    with col2:
        to_unit = st.selectbox("To", ["Celsius", "Fahrenheit", "Kelvin"])



#converted functions
def length_converter(value, from_unit, to_unit):
    # Length units ko conversion factor ke zariye convert karna
    length_units = {
        'Meters': 1, 'Kilometers': 0.001, 'Centimeters': 100, 'Millimeters': 1000,
        'Miles': 0.000621371, 'Yards': 1.09361, 'Feet': 3.28084, 'Inches': 39.3701
    }
    return (value / length_units[from_unit]) * length_units[to_unit]

def weight_converter(value, from_unit, to_unit):
    # Weight units ko conversion factor ke zariye convert karna
    weight_units = {
        'Kilograms': 1, 'Grams': 1000, 'Milligrams': 1000000, 'Pounds': 2.20462, 'Ounces': 35.274
    }
    return (value / weight_units[from_unit]) * weight_units[to_unit]

def temp_converter(value, from_unit, to_unit):
    #temperature conversion logic
    if from_unit == "Celsius":
        return (value * 9/5) + 32 if to_unit == "fahrenheit" else value + 273.15 if to_unit == "kelvin" else value
    elif from_unit == "fahrenheit":
        return (value - 32) * 5/9 if to_unit == "celsius" else ((value - 32) * 5/9) + 273.15 if to_unit == "kelvin" else value
    elif from_unit == "kelvin":
        return value - 273.15 if to_unit == "celsius" else (value - 273.15) * 9/5 + 32 if to_unit == "fahrenheit" else value
    return value



# Convert button (Conversion karne ka button)
if st.button("🔄 Convert"):
    if conversion_type == "Length":
        result = length_converter(value, from_unit, to_unit)
    elif conversion_type == "Weight":
        result = weight_converter(value, from_unit, to_unit)
    elif conversion_type == "Temperature":
        result = temp_converter(value, from_unit, to_unit)

    # Result ko dikhana (Conversion ka result show karna)
    st.markdown(f"<div class='result-box'>{value} {from_unit} = {result:.4f} {to_unit}</div>", unsafe_allow_html=True)

# Footer (Neeche footer message)
st.markdown("<div class='footer'>Created by Muhammad Asaad</div>", unsafe_allow_html=True)
 
    
    

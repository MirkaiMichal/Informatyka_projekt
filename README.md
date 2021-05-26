# Informatyka_projekt
    st.markdown(
        """
        <style>
        .reportview-container {
            background: url("https://resi.ze-robot.com/dl/4k/4k-desktop-wallpaper.-1920%C3%971200.jpg")
        }

        </style>
        """,
        unsafe_allow_html=True
    )
    
    st.write("""
             # Kalkulator walut
             by Michał Zmorzyński huehue
             """)
    
    currency_list = ['EUR', 'BGN', 'DKK', 'GBP', 'SEK', 'CZK', 'PLN', 'HUF', 'RON', 'HRK', 'RUB']
    base_price_unit = st.selectbox('Wybierz walutę do przeliczenia:', currency_list)
    symbols_price_unit = st.selectbox('Wybierz walutę, którą chcesz otrzymać:', currency_list)
    number = st.number_input('Kwota:')
    
    def przelicznik_walut(wartosc, w1, w2):
        c = CurrencyConverter()
        przelicznik = c.convert(wartosc, w1, w2)
        return round(przelicznik, 2)
    
    df = przelicznik_walut(number, base_price_unit, symbols_price_unit)
    
    #st.header('Currency conversion')
    #st.write(df)
    
    def user_input_features():
        data = {'     Z     ': base_price_unit,
                '     Na     ': symbols_price_unit,
                '     Ilość     ': number,
                '     Kwota     ': df}
        features = pd.DataFrame(data, index=[1])
        return features
    dx = user_input_features()
    
    st.write(dx)

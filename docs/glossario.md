# Glossário de Turismo (Turismês)

Dicionário oficial de termos técnicos e de negócio utilizados na CVC Corp e no mercado de turismo.

!!! info "Por que isso é importante?"
    Para analisar incidentes corretamente, você precisa distinguir um erro técnico de uma regra de negócio. Entender o que é um *No-Show* ou uma *Tarifa Net* ajuda a priorizar chamados com impacto financeiro.

---

## ✈️ Aéreo (GDS e Cias Aéreas)

**PNR (Passenger Name Record)**
: Também conhecido como "Localizador". É o código alfanumérico (Ex: `XJ59L2`) que identifica a reserva no sistema da companhia aérea.
: *Impacto na Sustentação:* Sem o PNR, não conseguimos rastrear logs no GDS (Amadeus/Sabre).

**GDS (Global Distribution System)**
: Os grandes sistemas que conectam as agências às companhias aéreas (Ex: Amadeus, Sabre, Galileo).
: *Nota:* Se o GDS cai, paramos de emitir passagens mundialmente.

**Bilhete (E-Ticket)**
: É o contrato final. Uma reserva (PNR) pode existir *sem* um bilhete emitido (apenas reservada), mas um passageiro só embarca com o Bilhete.
: *Erro comum:* "Reserva confirmada mas sem bilhete" = Passageiro não embarca.

**No-Show**
: Quando o passageiro não se apresenta para o embarque. Gera multas pesadas.

---

## 🏨 Hotelaria e Pacotes

**Voucher**
: Documento que comprova que o serviço foi pago e garante o uso pelo cliente.
: *Crítico:* Se o sistema de envio de voucher falha, o cliente pode ser barrado na recepção do hotel.

**Allotment**
: É um "bloqueio" ou contingente de quartos pré-negociados. Ex: A CVC tem 20 quartos garantidos no Hotel X até tal data.
: *Erro comum:* "Hotel indisponível" mesmo com vagas no site do hotel (significa que o nosso *allotment* acabou).

**Pax**
: Abreviação universal para "Passenger" ou "Passageiro/Hóspede".
: *Ex:* "Reserva para 2 Pax" (2 pessoas).

**Rooming List**
: Lista com os nomes dos hóspedes enviada ao hotel antes do check-in.

---

## 💰 Financeiro e Tarifas

**Tarifa NET (Net Rate)**
: É o preço de custo que a operadora paga ao fornecedor.
: *Atenção:* Essa tarifa **nunca** deve aparecer para o cliente final. Se aparecer, é incidente de segurança/negócio grave.

**Tarifa Comissionada**
: É a tarifa pública (cheia), da qual será descontada a comissão da agência.

**Markup**
: É a margem de lucro adicionada sobre a tarifa NET para chegar ao preço de venda.

**Repasse**
: Processo de pagamento ao fornecedor (hotel/cia aérea) após a venda.

---

## 🔄 Conectividade (API)

**Broker**
: Um intermediário que consolida vários hotéis ou serviços (Ex: Hotelbeds, Expedia). Nós conectamos no Broker, e o Broker conecta no hotel.

**Timeout**
: Tempo máximo que esperamos um fornecedor responder. No turismo, timeouts são frequentes porque dependemos de sistemas legados de terceiros.
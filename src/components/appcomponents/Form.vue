<template>
    <div class="container my-3">
        <div class="row">
            <div class="col-8">
                <h1>Aanmelden</h1>

                <h2>Gegevens</h2>
                <div class="form-group">
                    <h3>Reden van aanmelding</h3>
                    <div class="form-input my-4">
                        <label id="aanmeldreden-label" class="input__title">
                            Wat is de reden van uw aanvraag?
                        </label>
                        <div class="input__group">
                            <select class="form-control">
                                <option>
                                    Nieuwe werkgever met collectiviteit bij
                                    Zilveren Kruis
                                </option>
                                <option selected>
                                    Overstappen per 1-1-2023 naar Zilveren Kruis
                                </option>
                            </select>
                        </div>
                    </div>
                </div>
                <div class="form-group">
                    <h3>Persoonlijke gegevens</h3>
                    <div class="form-input my-4">
                        <div class="input__group">
                            <label class="input__title">Naam</label>
                            <input
                                class="input__field form-control"
                                type="text"
                                v-model="voornaam"
                            />
                        </div>
                    </div>
                    <div class="form-input my-4">
                        <div class="input__group">
                            <label class="input__title">Tussenvoegsels</label>
                            <input
                                class="input__field form-control"
                                type="text"
                                v-model="tussenvoegsels"
                            />
                        </div>
                    </div>
                    <div class="form-input my-4">
                        <div class="input__group">
                            <label class="input__title">Achternaam</label>
                            <input
                                class="input__field form-control"
                                type="text"
                                v-model="achternaam"
                            />
                        </div>
                    </div>
                    <div class="form-input my-4">
                        <div class="input__group">
                            <label class="input__title">Geslacht</label>
                            <div class="form-row">
                                <div class="radio custom-radio radio__option">
                                    <input
                                        id="man"
                                        class="radio__input custom-control-input"
                                        type="radio"
                                        name="geslacht"
                                        value="man"
                                        v-model="pickedGender"
                                    />
                                    <label
                                        class="radio__label custom-control-label"
                                        for="man"
                                    >
                                        Man
                                    </label>
                                </div>
                                <div class="radio custom-radio radio__option">
                                    <input
                                        id="vrouw"
                                        class="radio__input custom-control-input"
                                        type="radio"
                                        name="geslacht"
                                        value="vrouw"
                                        v-model="pickedGender"
                                    />
                                    <label
                                        class="radio__label custom-control-label"
                                        for="vrouw"
                                    >
                                        Vrouw
                                    </label>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="form-input my-4">
                        <div class="input__group">
                            <label class="input__title"> Geboortedatum </label>
                            <VueDatePicker v-model="date"></VueDatePicker>
                        </div>
                    </div>
                    <div class="form-input my-4">
                        <div class="input__group">
                            <label class="input__title">
                                Burgerservicenummer
                            </label>
                            <input
                                class="input__field form-control is-invalid"
                                type="text"
                                v-model="myBsn"
                                @keyup="handleSubmit"
                            />
                        </div>
                        <div
                            class="input__feedback invalid-feedback mt-1"
                            aria-live="polite"
                            :class="myClass"
                            v-if="bsnError"
                        >
                            <span>{{ bsnError }} </span>
                        </div>
                    </div>
                </div>

                <h2 class="mt-5">Verzekering</h2>
                <div class="form-group">
                    <h3>Basisverzekering</h3>
                    <p>
                        In Nederland is de basisverzekering verplicht. Iedereen
                        wordt voor de basisverzekering geaccepteerd. De overheid
                        bepaalt welke zorg hierin zit en dit is dus bij elke
                        verzekeraar hetzelfde.
                    </p>
                    <div class="input__group">
                        <label class="input__title">
                            Kies uw basisverzekering
                        </label>
                        <div class="form-row">
                            <div class="radio__tile">
                                <div class="radio custom-radio radio__option">
                                    <input
                                        value="Basis Budget"
                                        type="radio"
                                        name="radio-insurance"
                                        id="radio-insurance-basis-budget"
                                        class="radio__input custom-control-input"
                                        v-model="checked"
                                    />
                                    <label
                                        for="radio-insurance-basis-budget"
                                        class="radio__label custom-control-label"
                                    >
                                        <p class="radio__description">
                                            Basis Budget
                                        </p>
                                        <p class="radio__price">
                                            € 1.393,26 per jaar
                                        </p>
                                    </label>
                                </div>
                            </div>
                            <div class="radio__tile radio__tile--choice">
                                <div class="badge radio__tile-badge">
                                    Meest gekozen
                                </div>
                                <div class="radio custom-radio radio__option">
                                    <input
                                        value="Basis Zeker"
                                        type="radio"
                                        name="radio-insurance"
                                        id="radio-insurance-basis-zeker"
                                        class="radio__input custom-control-input"
                                        v-model="checked"
                                    />
                                    <label
                                        for="radio-insurance-basis-zeker"
                                        class="radio__label custom-control-label"
                                    >
                                        <p class="radio__description">
                                            Basis Zeker
                                        </p>
                                        <p class="radio__price">
                                            € 1.483,54 per jaar
                                        </p>
                                    </label>
                                </div>
                            </div>
                            <div class="radio__tile">
                                <div class="radio custom-radio radio__option">
                                    <input
                                        value="Basis Exclusief (Restitutie)"
                                        type="radio"
                                        name="radio-insurance"
                                        id="radio-insurance-basis-exclusief-(restitutie)"
                                        class="radio__input custom-control-input"
                                        v-model="checked"
                                    />
                                    <label
                                        for="radio-insurance-basis-exclusief-(restitutie)"
                                        class="radio__label custom-control-label"
                                    >
                                        <p class="radio__description">
                                            Basis Exclusief (Restitutie)
                                        </p>
                                        <p class="radio__price">
                                            € 1.624,62 per jaar
                                        </p>
                                    </label>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="form-group">
                    <div class="form-input my-4">
                        <div class="input__group">
                            <label class="input__title">
                                Kies je betaaltermijn
                            </label>
                            <select
                                class="form-control"
                                v-model="selectedTermijn"
                            >
                                <option>per maand</option>
                                <option>per kwartaal</option>
                                <option selected>per jaar</option>
                            </select>
                        </div>
                    </div>
                </div>
                <div v-if="checked" class="form-group">
                    <h3>Eigen risico</h3>
                    <div class="form-input my-4">
                        <div class="input__group">
                            <label class="input__title">
                                Kies de hoogste van het eigen risico
                            </label>
                            <select
                                class="form-control"
                                v-model="selectedRisico"
                            >
                                <option>€ 385 - verplicht eigen risico</option>
                                <option>
                                    € 885 - korting van € 22 per jaar
                                </option>
                            </select>
                        </div>
                    </div>
                </div>
                <div class="form-group">
                    <h3>Aanvullende verzekering</h3>
                    <p>
                        Onze aanvullende verzekeringen kennen ruim 100
                        verschillende vergoedingen. De hoogte van de vergoeding
                        verschilt per pakket.hoogte van de vergoeding verschilt
                        per pakket
                    </p>
                    <div class="form-input my-4">
                        <div class="input__group">
                            <label class="input__title">
                                Kies uw aanvullende verzekering
                            </label>
                            <select class="form-control" v-model="selectedAV">
                                <option selected>
                                    Geen aanvullende verzekering geselecteerd
                                </option>
                                <option>Aanvullend 1 - € 21,38 per jaar</option>
                                <option>Aanvullend 2 - € 85,06 per jaar</option>
                                <option>
                                    Aanvullend 3 - € 198,63 per jaar
                                </option>
                                <option>
                                    Aanvullend 4 - € 359,73 per jaar
                                </option>
                            </select>
                        </div>
                    </div>
                </div>
                <div class="form-group">
                    <div class="form-input my-4">
                        <div class="input__group">
                            <label class="input__title">
                                Kies uw tandartsverzekering
                            </label>
                            <select class="form-control" v-model="selectedTand">
                                <option selected>
                                    Geen tandartsverzekering geselecteerd
                                </option>
                                <option>Tand 1 - € 80,28 per jaar</option>
                                <option>Tand 2 - € 221,65 per jaar</option>
                                <option>Tand 3 - € 449,36 per jaar</option>
                            </select>
                        </div>
                    </div>
                </div>

                <h2 class="mt-5">Controleren</h2>
                <div class="form-group">
                    <h3>Gekozen pakket</h3>
                    <div v-if="checked">{{ checked }}</div>
                    <div>Betaaltermijn: {{ selectedTermijn }}</div>
                    <div>{{ selectedRisico }}</div>
                    <div>{{ selectedAV }}</div>
                    <div>{{ selectedTand }}</div>
                </div>
                <div class="form-group">
                    <h3>Totaalpremie</h3>
                </div>
                <div class="form-group">
                    <h3>Adres en contactgegevens</h3>
                    <div>
                        Naam: {{ voornaam }} {{ tussenvoegsels }}
                        {{ achternaam }}
                    </div>
                    <div>Geboortedatum: {{ date }}</div>
                    <div>Geslacht: {{ pickedGender }}</div>
                    <div>Burgerservicenummer: {{ myBsn }}</div>
                </div>
            </div>
        </div>
        <div class="col-4">
            <div class="card card--filled-secondary h-auto">
                <div class="card-body">
                    <div class="sf-contactblok-content">
                        <h3 class="mb-2">We staan voor je klaar</h3>
                        <p class="mb-5">Twijfel je? Heb je een vraag?</p>
                        <div class="phonenumber mb-2">
                            <a href="tel:0900 040 03 09">
                                <span class="sr-only"> Telefoonnummer </span>
                                0900 040 03 09
                            </a>
                            <div class="popover__container ml-1">
                                <button
                                    id="info-phone"
                                    type="button"
                                    class="btn popover__btn btn--popover btn-none"
                                >
                                    <span class="sr-only">
                                        Informatie weergeven
                                    </span>
                                </button>
                            </div>
                        </div>
                        <small>
                            Open op maandag t/m vrijdag van 08:00 tot 17:00
                        </small>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import VueDatePicker from '@vuepic/vue-datepicker';
import '@vuepic/vue-datepicker/dist/main.css';

export default {
    name: 'Form',
    components: { VueDatePicker },
    data() {
        return {
            voornaam: '',
            tussenvoegsels: '',
            achternaam: '',
            date: null,
            myBsn: '',
            myClass: 'valid',
            bsnError: '',
            checked: false,
            pickedGender: '',
            selectedRisico: '',
            selectedTermijn: '',
            selectedAV: '',
            selectedTand: ''
        };
    },
    methods: {
        handleSubmit() {
            this.bsnError =
                this.myBsn.length === 9
                    ? ''
                    : 'Helaas is het ingevoerde burgerservicenummer niet geldig. Probeer het opnieuw.';
        }
    }
};
</script>

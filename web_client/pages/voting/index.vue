<template>
    <div class="tw-min-h-screen tw-flex tw-flex-col">
        <Header>Citizen Portal - Voter Registration</Header>
        <div
            id="main-content"
            class="grid-container tw-mt-4 tw-flex-1 tw-w-full tw-flex tw-justify-center"
        >
            <form class="usa-form usa-form--large" @submit="checkForm">
                <fieldset class="usa-fieldset">
                    <legend class="usa-legend">
                        What party do you wish to register with?
                    </legend>
                    <p class="tw-text-ink tw-mt-4 tw-mb-6">
                        Registering with a party allows you to select a
                        candidate from that party to run in the general
                        election, and then vote for whoever you chose in the
                        general election, regardless of party affiliation.
                    </p>

                    <legend class="usa-sr-only">Voter Registration</legend>
                    <div
                        v-for="(party, index) in parties"
                        :key="index"
                        class="usa-radio"
                    >
                        <input
                            :id="party"
                            v-model="checked"
                            class="usa-radio__input"
                            type="radio"
                            name="voter-registration"
                            :value="party"
                        />
                        <label class="usa-radio__label" :for="party">{{
                            party
                        }}</label>
                    </div>

                    <div class="tw-flex tw-flex-col tw-items-end tw-mt-6">
                        <p class="tw-text-ink tw-text-sm">
                            Who are my current representatives?
                        </p>
                        <div class="tw-mt-6">
                            <button
                                class="tw-text-ink tw-underline"
                                type="submit"
                            >
                                Next
                            </button>
                        </div>
                    </div>
                </fieldset>
            </form>
        </div>
        <Footer />
    </div>
</template>

<script>
import Header from '../../components/Header'
import Footer from '../../components/Footer'

export default {
    name: 'Index',
    components: { Footer, Header },
    data() {
        return {
            errors: [],
            parties: [
                'Constitution Party',
                'Democratic Party',
                'Green Party',
                'Libertarian Party',
                'Republican Party',
            ],
            checked: 'Democratic Party',
        }
    },
    methods: {
        checkForm(e) {
            this.errors = []
            this.$router.push({ path: '/voting/reps' })

            e.preventDefault()
        },
    },
}
</script>

<style scoped></style>

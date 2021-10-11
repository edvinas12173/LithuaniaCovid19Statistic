<template>
    <div class="col-md-12 mt-5">
        <div class="alert alert-primary d-flex align-items-center mb-3" role="alert">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" class="bi bi-exclamation-triangle-fill flex-shrink-0 me-2" viewBox="0 0 16 16" role="img" aria-label="Warning:">
                <path d="M8.982 1.566a1.13 1.13 0 0 0-1.96 0L.165 13.233c-.457.778.091 1.767.98 1.767h13.713c.889 0 1.438-.99.98-1.767L8.982 1.566zM8 5c.535 0 .954.462.9.995l-.35 3.507a.552.552 0 0 1-1.1 0L7.1 5.995A.905.905 0 0 1 8 5zm.002 6a1 1 0 1 1 0 2 1 1 0 0 1 0-2z"/>
            </svg>
            <div>
                Every <b>15 minutes</b> updated statistic about Coronavirus
            </div>
        </div>
        <div class="p-2 bg-dark mb-3 rounded-sm shadow-lg">
            <div class="text-center text-white text-uppercase mt-2">
                <h1>Lithuania Covid-19 Statistic</h1>
            </div>
            <div class="p-3">
                <div class="row">
                    <div class="col-md-4 mt-2">
                        <div class="card shadow-lg">
                            <div class="card-body">
                                Total Cases: <b>{{lithuania.TotalCases}}</b>
                            </div>
                        </div>
                    </div>
                    <div class="col-md-4 mt-2">
                        <div class="card shadow-lg">
                            <div class="card-body">
                                Total Deaths: <b>{{lithuania.TotalDeaths}}</b>
                            </div>
                        </div>
                    </div>
                    <div class="col-md-4 mt-2">
                        <div class="card shadow-lg">
                            <div class="card-body">
                                Total Recovered: <b class="text-success">{{lithuania.TotalRecovered}}</b>
                            </div>
                        </div>
                    </div>
                    <div class="col-md-4 mt-2">
                        <div class="card shadow-lg">
                            <div class="card-body">
                                Active Cases: <b>{{lithuania.ActiveCases}}</b>
                            </div>
                        </div>
                    </div>
                    <div class="col-md-4 mt-2">
                        <div class="card shadow-lg">
                            <div class="card-body">
                                New Cases: <b>{{lithuania.NewCases}}</b>
                            </div>
                        </div>
                    </div>
                    <div class="col-md-4 mt-2">
                        <div class="card shadow-lg">
                            <div class="card-body">
                                New Deaths: <b>{{lithuania.NewDeaths}}</b>
                            </div>
                        </div>
                    </div>
                    <div class="col-md-4 mt-2">
                        <div class="card shadow-lg">
                            <div class="card-body">
                                New Recovered: <b class="text-success">{{lithuania.NewRecovered}}</b>
                            </div>
                        </div>
                    </div>
                    <div class="col-md-4 mt-2">
                        <div class="card shadow-lg">
                            <div class="card-body">
                                Serious Critical: <b>{{lithuania.Serious_Critical}}</b>
                            </div>
                        </div>
                    </div>
                    <div class="col-md-4 mt-2">
                        <div class="card shadow-lg">
                            <div class="card-body">
                                Infection Risk: <b class="text-danger">{{lithuania.Infection_Risk}}%</b>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="p-2 bg-dark mb-3 rounded-sm shadow-lg">
            <div class="text-center text-white text-uppercase mt-2">
                <h1>World Covid-19 Statistic</h1>
            </div>
            <div class="p-3">
                <div class="row">
                    <div class="col-md-4 mt-2">
                        <div class="card shadow-lg">
                            <div class="card-body">
                                Total Cases: <b>{{world.TotalCases}}</b>
                            </div>
                        </div>
                    </div>
                    <div class="col-md-4 mt-2">
                        <div class="card shadow-lg">
                            <div class="card-body">
                                Total Deaths: <b>{{world.TotalDeaths}}</b>
                            </div>
                        </div>
                    </div>
                    <div class="col-md-4 mt-2">
                        <div class="card shadow-lg">
                            <div class="card-body">
                                Total Recovered: <b class="text-success">{{world.TotalRecovered}}</b>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="text-center">
            <a class="text-white" href="https://github.com/edvinas12173">Github</a>
            |
            <a class="text-white" href="https://vaccovid.live/">VACCOVID</a>
        </div>
    </div>
</template>

<script>
    const lithuaniaStatistic = {
        method: 'GET',
        url: 'https://vaccovid-coronavirus-vaccine-and-treatment-tracker.p.rapidapi.com/api/npm-covid-data/country-report-iso-based/Lithuania/ltu',
        headers: {
            'x-rapidapi-host': 'vaccovid-coronavirus-vaccine-and-treatment-tracker.p.rapidapi.com',
            'x-rapidapi-key': '14531217dfmsh888bc94be665512p162129jsn1783e037b436'
        }
    }
    const worldStatistic = {
        method: 'GET',
        url: 'https://vaccovid-coronavirus-vaccine-and-treatment-tracker.p.rapidapi.com/api/npm-covid-data/world',
        headers: {
            'x-rapidapi-host': 'vaccovid-coronavirus-vaccine-and-treatment-tracker.p.rapidapi.com',
            'x-rapidapi-key': '14531217dfmsh888bc94be665512p162129jsn1783e037b436'
        }
    }
    export default {
        data() {
            return {
                lithuania: [],
                world: [],
            }
        },
        mounted() {
            axios.request(lithuaniaStatistic)
                .then(response => {
                    this.lithuania = response.data[0]
                })
                .catch(function (error) {
                    console.error(error);
                });
            axios.request(worldStatistic)
                .then(response => {
                    this.world = response.data[0]
                })
                .catch(function (error) {
                    console.error(error);
                });
        }
    }
</script>

<template>
    <nav class="navbar is-fixed">
        <div class="container">
        <div class="navbar-brand">
            <!-- BAKD Branding -->
            <router-link :to="{ name: 'homepage' }" class="navbar-item">
                <img src="/images/branding/logo-200w.png" style="max-height: 3rem;" :alt="appName" :title="appName">
            </router-link>

            <!-- Navbar Hamburgler -->
            <!-- TODo: Wire me up -->
            <a role="button" class="navbar-burger burger" aria-label="menu" aria-expanded="false" data-target="navMainMenu">
              <span aria-hidden="true"></span>
              <span aria-hidden="true"></span>
              <span aria-hidden="true"></span>
            </a>
        </div>

        <!-- Main Navbar Menu Items -->
        <div id="navMainMenu" class="navbar-menu">
            
            <!-- Navbar Left Side -->
            <div class="navbar-start">

              <!-- Search Input -->
              <!-- TODO: Wire me up -->
              <b-field class="level-item" style="margin-bottom: 0 !important;">
                <b-input placeholder="Search..."
                    type="search" 
                    icon="magnify">
                </b-input>
              </b-field>

              <!-- "More" Dropdown Menu Item -->
              <div class="navbar-item has-dropdown is-hoverable">
                <a class="navbar-link more-link">
                  More
                </a>
                <div class="navbar-dropdown">

                  <!-- <a class="navbar-item"> -->
                  <router-link :to="{ name: 'campaigns.directory' }" class="text-dark has-link navbar-item">
                    <div class="media">
                        <div class="media-left">
                            <fa icon="building" style="width: 20px;" />
                        </div>
                        <div class="media-content">
                            <h3 style="font-weight: 700;">Campaign Directory</h3>
                            <span style="font-weight: 300;">Find a project to contribute to or get involved with.</span>
                        </div>
                    </div>
                  <!-- </a> -->
                  </router-link>

                  <hr class="navbar-divider">

                  <!-- <a class="navbar-item"> -->
                  <router-link :to="{ name: 'members.directory' }" class="text-dark has-link navbar-item">
                    <div class="media">
                        <div class="media-left">
                            <fa icon="users" style="width: 20px;" />
                        </div>
                        <div class="media-content">
                            <h3 style="font-weight: 700;">Member Directory</h3>
                            <span style="font-weight: 300;">Find people to help with your project, or just exchange ideas.</span>
                        </div>
                    </div>
                  <!-- </a> -->
                  </router-link>

                  <hr class="navbar-divider">
                  
                  <!-- <a class="navbar-item"> -->
                  <router-link :to="{ name: 'campaigns.create' }" class="text-dark has-link navbar-item">
                    <div class="media">
                      <div class="media-left">
                        <fa icon="chart-line" style="width: 20px;" />
                      </div>
                      <div class="media-content">
                        <h3 style="font-weight: 700;">Start a Campaign</h3>
                        <span style="font-weight: 300;">Get the funding you need to build out your idea.</span>
                      </div>
                    </div>
                  <!-- </a> -->
                  </router-link>

                  <hr class="navbar-divider">
                  
                  <!-- <a class="navbar-item"> -->
                  <router-link :to="{ name: 'bounties.all' }" class="text-dark has-link navbar-item">
                    <div class="media">
                      <div class="media-left">
                        <fa icon="trophy" style="width: 20px;" />
                      </div>
                      <div class="media-content">
                        <h3 style="font-weight: 700;">Bounties <b-tag class="is-success is-tiny">LIVE</b-tag></h3>
                        <span style="font-weight: 300;">Don't miss out on your chance to win free <strong>BAKD</strong> Coins!</span>
                      </div>
                    </div>
                  <!-- </a> -->
                  </router-link>
                  
                  <hr class="navbar-divider">
                  
                  <!-- <a class="navbar-item"> -->
                  <router-link :to="{ name: 'how-it-works' }" class="text-dark has-link navbar-item">
                    <div class="media">
                      <div class="media-left">
                        <fa icon="question-circle" style="width: 20px;" />
                      </div>
                      <div class="media-content">
                        <h3 style="font-weight: 700;">How it Works</h3>
                        <span style="font-weight: 300;">Learn the in's and out's of running a <strong>BAKD</strong> Campaign.</span>
                      </div>
                    </div>
                  </router-link>
                  <!-- </a> -->

                </div>
              </div>
            </div>

            <!-- Navbar Right -->
            <div class="navbar-end">
                <!-- <locale-dropdown/>  -->
  
              <template v-if="user">              
                <!-- MESSAGES NAV DROPDOWN -->
                <a href="#" class="navbar-item text-dark is-dark"><fa icon="envelope"  class="is-size-5" /></a>
                
                <!--  NOTIFICATIONS NAV DROPDOWN -->
                <a href="#" class="text-dark is-dark navbar-item" style="margin-right: 20px;">
                  <fa icon="inbox" class="is-size-5" />
                </a>
              </template>



                <!-- Authenticated -->
                <b-dropdown v-if="user" class="level-item navbar-item" position="is-bottom-left" hoverable>
                  <a class="media navbar-item profile-photo main-dropdown-link" slot="trigger">
                    <div class="media-left level-item">
                        <!-- {{ user.name }}  -->
                        0.000 BAKD
                    </div>
                    <div class="media-content level-item">
                      <img :src="user.photo_url"> 
                    </div>
                    <div class="media-right level-item">
                        <b-icon icon="chevron-down"></b-icon>
                    </div>
                  </a>

                  <b-dropdown-item custom>
                    <router-link :to="{ name: 'members.dashboard' }" class="nav-item has-link has-text-dark">
                      <div class="media" style="margin-bottom: -.35rem;">
                          <div class="media-left dropdown-avatar">
                              <img :src="user.photo_url" style="max-height: 2.75rem;"> 
                          </div>
                          <div class="text-dark media-content avatar-info">
                            <h3>{{ user.name }}</h3>
                            <small>Community Member</small> 
                          </div>
                      </div>
                    </router-link>
                  </b-dropdown-item>
                  
                  <b-dropdown-item separator />

                  <b-dropdown-item has-link>
                    <router-link :to="{ name: 'members.profile' }" class="text-dark">
                      <fa icon="users" style="width: 20px;" />
                      {{ $t('My Profile') }}
                    </router-link>
                  </b-dropdown-item>

                  <b-dropdown-item has-link>
                    <router-link :to="{ name: 'campaigns.directory' }" class="text-dark">
                      <fa icon="building" style="width: 20px;" />
                      {{ $t('My Campaigns') }}
                    </router-link>
                  </b-dropdown-item>

                  <b-dropdown-item has-link>
                    <router-link :to="{ name: 'members.settings' }" class="text-dark">
                      <fa icon="cog" style="width: 20px;" />
                      {{ $t('Privacy Settings') }}
                    </router-link>
                  </b-dropdown-item>

                  <b-dropdown-item has-link>
                    <router-link :to="{ name: 'bounties.dashboard' }" class="text-dark">
                      <fa icon="trophy" style="width: 20px;" />
                      {{ $t('Bounty Dashboard') }}
                    </router-link>
                  </b-dropdown-item>
                  
                  <b-dropdown-item separator />
                  
                  <b-dropdown-item has-link>
                    <a href="#" @click.prevent="logout" class="text-dark">
                      <fa icon="sign-out-alt" style="width: 20px;" />
                      {{ $t('logout') }}
                    </a>
                  </b-dropdown-item>

                </b-dropdown>

                <!-- Guest -->
                <div v-else class="level-item navbar-item">
                    <div class="buttons">
                      <router-link :to="{ name: 'register' }" class="button is-rounded is-primary" style="font-weight: 400 !important;" active-class="active">
                        {{ $t('register') }}
                      </router-link>
                      <router-link :to="{ name: 'login' }" class="button is-rounded is-light" style="font-weight: 400 !important;" active-class="active">
                        {{ $t('login') }}
                      </router-link>
                    </div>
                </div>

            </div>
        </div>
    </div>
    </nav>
</template>

<script>
import { mapGetters } from 'vuex'
import LocaleDropdown from '../elements/LocaleDropdown'

export default {
  components: {
    LocaleDropdown
  },

  data: () => ({
    navigation: 'home',
    appName: window.config.appName,
  }),

  computed: mapGetters({
    user: 'auth/user'
  }),

  methods: {
    async logout () {
      // Log out the user.
      await this.$store.dispatch('auth/logout')

      // Redirect to login.
      this.$router.push({ name: 'login' })
    },

    viewUserProfile() {
        // TODO...    
    },
  }
}
</script>


<style scoped lang="scss">
@import './resources/sass/variables';

nav {
  top: 0;
  border-top: 3px solid $primary;
}

.button {
  font-weight: 500 !important;
}

.navbar.is-fixed {
    position: fixed;
    width: 100%;
  
    button {
      font-weight: 400 !important;
    }
}

.navbar-brand {
  img {
    width: 100%;
    height: auto;
    max-width: 130px;
    max-height: 45px;
  }
}

.main-dropdown-link,
.more-link,
.navbar-link {
    background: transparent !important;
    background-color: transparent !important;

    &:hover,
    &:focus,
    &:active {
        background: transparent !important;
        background-color: transparent !important;
    }
}

.dropdown-menu {
    -webkit-box-shadow: 0 8px 8px rgba(10, 10, 10, 0.1);
    box-shadow: 0 8px 8px rgba(10, 10, 10, 0.1);
    border-bottom-left-radius: 6px;
    border-bottom-right-radius: 6px;
    right: 15px;
    min-width: 11rem;
}

.navbar-dropdown {
    min-width: 12rem;
    max-width: 18rem;
    width: 420px;

    span {
        white-space: normal;
    }
}

.dropdown.is-bottom-left .dropdown-menu {
    right: 15px !important;
    left: auto;
}

.profile-photo {
    margin-left: -30px;
    
    .media-left {
        margin-right: .5rem;
    }    

    .media-right {
        margin-left: .5rem;
    }

    img {
      border-radius: 50%;
    }
}

span.tag {
    &.is-tiny {
        height: unset;
        padding: 2px 8px;

        span {
            font-weight: 600;
            font-size: .65rem;
        }
    }
}

.dropdown-avatar img {
    border: 1px solid #cdcdcd;
    border-radius: 3px;
}

.avatar-info {
    margin-left: -2px;

    h3 {
        padding-bottom: 1px;
        margin-bottom: -4px;
        padding-top: 3px;
        font-weight: 400;
    }

    small {
        margin-top: 0px;
        padding-top: 0px;
        font-weight: 700;
    }
}
.navbar-burger {
    color: #4a4a4a;
    cursor: pointer;
    height: auto;
    position: relative;
    width: 4rem;
    margin-left: auto;
}
</style>
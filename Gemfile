source 'https://rubygems.org'

# In this case Bundler do it wrong
# It cannot find correct path to gems
#
# It works right with 1.11.2, and it does it wrong in >= 1.12.0
eval_gemfile "./Gemfiles/specific_1.rb"

# WORKAROUND:
#
# If I put all my specific files in `root` folder than Bundler do it right
# Looks like, it this case Bundler can find right paths
#
# eval_gemfile "./specific_3.rb"

# NOTES:
# export BUNDLE_GEMFILE=/PATH/TO/RELEASES/RAILS_CMS/current/Gemfile
# env | grep BUNDLE_GEMFILE
# unset  BUNDLE_GEMFILE
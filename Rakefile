# Add your own tasks in files placed in lib/tasks ending in .rake,
# for example lib/tasks/capistrano.rake, and they will automatically be available to Rake.

require File.expand_path('../config/application', __FILE__)

Rails.application.load_tasks
require 'nokogiri'
require 'pry'

namespace :museumScraper do

  desc "Srapes museum for name"
  task :scrapeMoMa do
    # stored physical HTML in a text file
    html = File.open("moma_museum/visit_moma.text","r"){|file| file.read}
    # parsing that file
    data = Nokogiri::HTML(html)
    # I got a messy string so I squeezed all extra space
    # and removed newline char
    info_array = data.css('div.visit-section').text.squeeze.split("\n ")

    moma_museum ={}

    moma_museum[:name] = info_array[1]
    moma_museum[:location] = info_array[3..4].join(', ')
    moma_museum[:number] = info_array[5].split(' | ')[0]
    
    Museum.create(moma_museum)

  end

  desc "Scrapes each exhibitions: name,date,img,desc,museum_id"
  task :scrapeExhibition do 
    # Below is all possible sudo code
    html = File.open("moma_museum/exhibition1.text","r"){|file| file.read}
    data = Nokogiri::HTML(html)
    list_of_exhibitions = []

    data.css('span.no-image').each do |exhibition|
      new_exhibition = {}
      new_exhibition[:name] = 
      new_exhibition[:date] =
      new_exhibition[:image] =
      new_exhibition[:description] =
      new_exhibition[:museum_id] =

      list_of_exhibitions << new_exhibition
    end

  end
end
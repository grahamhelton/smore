---
title: "Blog title: researching the XYZ"
date: 2021-12-06 
tags: ["Homelab","Security","Research"]
description: "Short description of post."
draft: false 
type: page
---

# Title
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla eu sem viverra, blandit justo in, ullamcorper nisl. Aliquam maximus lorem et molestie pretium. In luctus facilisis eros id finibus. Nam ac lectus lacus. Nullam quis egestas risus. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Fusce id elit gravida sem gravida sollicitudin. Sed congue nulla elit, id cursus nibh viverra vitae.

# Title
In vel sapien a justo condimentum finibus. Fusce non magna a leo suscipit fringilla nec in magna. Vestibulum viverra dapibus magna in placerat. Pellentesque sed sodales ex. Vivamus blandit eu justo ac luctus. Etiam nec tellus molestie, suscipit velit ut, lacinia velit. Quisque libero tellus, hendrerit ac dignissim et, faucibus ac nulla. Vestibulum finibus posuere varius. Maecenas finibus est non egestas aliquet. Cras venenatis metus sed iaculis fermentum. In ipsum dui, sagittis ac augue id, feugiat bibendum dui. Sed pellentesque orci orci, quis mollis massa tempor mattis.

```python
#! /bin/python3.10
import re
import requests
import os
from os.path import exists
from bs4 import BeautifulSoup
from colorama import Fore, Style
company_list = ['scythe','dragos']
company_url = {'scythe':'https://www.scythe.io/about/careers','dragos':'https://jobs.lever.co/dragos'}

# Define formatting
reset = Style.RESET_ALL
green = Fore.GREEN
purple = Fore.MAGENTA
sep = Fore.BLUE + "---------------------------" + reset

def get_format(response,company_name):
    '''Return the HTML attribute needed for each site'''
    match company_name:
       case "scythe":
            soup = BeautifulSoup(response.text, 'html.parser').findAll("h3",attrs={"id": "w-node-_6a3848d7-bd9c-4061-be22-05d0c32b7a82-c32b7a81"})
            return soup
       case "dragos":
            soup = BeautifulSoup(response.text, 'html.parser').findAll("h5",attrs={"data-qa": "posting-name"})
            return soup

def parse(posting_location,company_name):
    '''Issue the HTML request for job posting page'''
    # Issue request to scyhte careers page 
    response = requests.get(posting_location,company_name)

    # Get the format of the specific site to parse
    parsed_response = get_format(response,company_name)

    return parsed_response 

def parse_html(html_response):
    '''Takes list of HTML strings and parses them to contain just the job posting'''
    # for each job posting
    postings_list = []
    for i in html_response:
        # Remove HTML from job posting 
        postings_list.append(re.sub('<[^<]+?>', '', str(i)))
    return postings_list

def get_new(postings_list,old_list,company_name):
    '''Get the difference in the new job postings and the old ones'''
    new_post = list(set(postings_list) - set(old_list)) + list(set(old_list) - set(postings_list)) 
    path = './data/'+company_name 

    # Save job posting to file
    with open(path, 'w') as f:
        for listing in postings_list:
            f.write("%s \n" % listing)
    if new_post:
        return company_name,new_post 

def get_old(company_name):
    '''Get the previous job postings and add them to a list'''
    # If data file does not exist, create it
    path = './data/'+company_name
    if not exists(path):
        open(path, 'a').close()
    with open(path) as file:
        lines = file.readlines()
        old_list = []
        for i in lines:
            # for each job posting, strip out the characters we don't need 
            old_list.append(i.rstrip())
    return old_list

def print_results(company_name,new_post):
    '''print the job postings'''
    company_name = str(new_post[0]).upper()
    print(f"{green}{company_name} has new job postings!")
    print(sep)
    new_post = new_post[1:]
    job_postings = list(new_post)
    for i in job_postings:
        print(f"{purple}",*i,sep="\n")
    print(sep)
    pass

def select_company():
    '''Select the company passed in list and then call the function required for that specific job'''
    # Get the company name from the index number passed in through the function
    for company in range(len(company_list)):
        company_name = list(company_url.keys())[company]
        posting_location = list(company_url.values())[company]
        html_response = parse(posting_location,company_name)
        old_list = get_old(company_name)
        postings_list = parse_html(html_response)
        new_post = get_new(postings_list,old_list,company_name)
        if new_post:
            print_results(company_name,new_post)
        else:
            print(f"{green}{company_name}{purple} has no new job postings")

print(f"{green}Ear2Ground:{purple} A Program to help you keep tabs on the job postings of infosec companies")
print(sep)
def main():
    path = './data/'
    if not os.path.exists(path):
        os.makedirs(path)
    select_company()

if __name__ == "__main__":
    main()

```


Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Nunc aliquam, urna a ultricies dictum, mi arcu commodo eros, dictum vulputate leo magna ac orci. Quisque ultricies molestie nibh, eget sagittis est commodo ut. Cras fermentum, lectus eu interdum rhoncus, erat tortor aliquam velit, eu iaculis purus ex sed lorem. Nunc maximus nisi eu mauris ultricies, non placerat nisl fringilla. Quisque dignissim tellus enim, ut faucibus diam iaculis sit amet. Aenean vestibulum et nunc tempor elementum. Mauris vel augue id justo tempor euismod. Nunc elementum vulputate ante sit amet pulvinar. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Fusce vitae faucibus lectus.
1. This
2. Is
3. A
4. List
## Smaller Title 2
- This
- Is
- Also
- A
- List 

Sed imperdiet metus at porta blandit. Proin aliquet fringilla fringilla. In eu mi tempus, condimentum leo in, fermentum purus. Fusce eget dignissim quam. Nulla faucibus elit vel ligula laoreet tempor. Phasellus sed magna velit. Donec at euismod mi. Cras suscipit interdum ligula.
> This is a block quote. Groovy.

In ac euismod diam, quis vehicula tellus. Duis mollis, nulla quis egestas congue, eros enim tempor urna, ac pretium elit mi quis nulla. Nunc id vestibulum felis. Aliquam quis massa at dui posuere mattis. Curabitur fermentum rutrum nisl, nec hendrerit velit vestibulum ut. Donec varius euismod ex, eget lacinia odio scelerisque eget. Cras posuere, massa tincidunt tristique semper, tellus felis porta lorem, eu pulvinar velit lacus sit amet orci. Ut finibus dolor ac lectus tristique, non condimentum justo tristique. Pellentesque consectetur mollis tincidunt. Praesent dapibus, dui sed rhoncus luctus, erat ligula posuere eros, quis ullamcorper justo leo id tellus. 
